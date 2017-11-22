---
UID: NF.wdfdmatransaction.WdfDmaTransactionDmaCompleted
title: WdfDmaTransactionDmaCompleted
author: windows-driver-content
description: The WdfDmaTransactionDmaCompleted method notifies the framework that a device's DMA transfer operation is completed.
old-location: wdf\wdfdmatransactiondmacompleted.htm
ms.assetid: 83c1c4cb-b28b-4980-92fb-a1a49d95406e
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdmatransaction.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfDmaTransactionDmaCompleted
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfDmaTransactionDmaCompleted
req.iface: 
req.product: Windows 10 or later.
---

# WdfDmaTransactionDmaCompleted function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDmaTransactionDmaCompleted</b> method notifies the framework that a device's DMA transfer operation is completed.  </p>


## -syntax

````
BOOLEAN WdfDmaTransactionDmaCompleted(
  _In_  WDFDMATRANSACTION DmaTransaction,
  _Out_ NTSTATUS          *Status
);
````


## -parameters
<dl>

### -param <i>DmaTransaction</i> [in]

<dd>
<p>A handle to a DMA transaction object that the driver obtained from a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>.</p>
</dd>

### -param <i>Status</i> [out]

<dd>
<p>A pointer to a location that receives the status of the DMA transfer. For more information, see the following Remarks section.</p>
</dd>
</dl>

## -returns
<p><b>WdfDmaTransactionDmaCompleted</b> returns <b>FALSE</b> and <i>Status</i> receives STATUS_MORE_PROCESSING_REQUIRED if additional transfers are needed to complete the DMA transaction. The method returns <b>TRUE</b> if no additional transfers are required. </p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>Framework-based drivers must call one of the following methods whenever a <a href="wdf.dma_transactions_and_dma_transfers">DMA transfer</a> is complete:</p>

<p><b>WdfDmaTransactionDmaCompleted</b></p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547049">WdfDmaTransactionDmaCompletedFinal</a>
</p>

<p>Typically, drivers call these methods from within an <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> event callback function, after a device interrupt indicates the completion of a DMA transfer operation. A driver for a system-mode DMA device might call these methods from within an <a href="https://msdn.microsoft.com/C638A505-AAE1-48FC-B06B-F2F161ADC948">EvtDmaTransactionDmaTransferComplete</a> event callback function.</p>

<p>The framework might divide a <a href="wdf.dma_transactions_and_dma_transfers">DMA transaction</a> into several DMA transfer operations. Therefore, the driver must examine the method's return value to determine if additional transfers are required. </p>

<p>If the method returns <b>FALSE</b>, the <i>Status</i> location receives STATUS_MORE_PROCESSING_REQUIRED and additional DMA operations are required to complete the transaction. Typically, the <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> event callback function does nothing else at this point. Instead, the framework calls the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function, so the callback function can begin the next transfer. </p>

<p>If the method returns <b>TRUE</b>, no more transfers will occur for the specified transaction. In this case, a <i>Status</i> value of STATUS_SUCCESS means that the framework did not encounter any errors and the DMA transaction is complete. </p>

<p>If the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/hh439264">WdfDmaTransactionStopSystemTransfer</a> before calling <b>WdfDmaTransactionDmaCompleted</b>, <b>WdfDmaTransactionDmaCompleted</b> returns <b>TRUE</b> and a <i>Status</i> value of <b>STATUS_CANCELLED</b>.</p>

<p>For transactions that were set for <a href="https://msdn.microsoft.com/windows/hardware/drivers/wdf/">single transfer</a>, <b>WdfDmaTransactionDmaCompleted</b> returns <b>TRUE</b> and a <i>Status</i> value of <b>STATUS_WDF_TOO_MANY_TRANSFERS</b> if the hardware fails to complete the transaction in a single transfer, even though initialization succeeded.
 	This could happen for hardware that reports residual transfers for each DMA operation. For example, the driver programs the device to write 64KB, but the device writes only 60KB.
   In this case, the driver might repeat the DMA operation or reset the device.</p>

<p>Any other value for <i>Status</i> means that the framework detected an error and the DMA transaction might not have been completed.</p>

<p>When <b>WdfDmaTransactionDmaCompleted</b> returns <b>TRUE</b>, the driver typically does the following:</p>

<p>Calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff548734">WdfObjectDelete</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a> to delete or reuse the transaction object, respectively.</p>

<p>Completes the I/O request, if the DMA transaction is associated with an I/O request. (Drivers complete requests by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549945">WdfRequestComplete</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a>.)</p>

<p>For more information about completing DMA transfers, see <a href="NULL">Completing a DMA Transfer</a>.</p>

<p>The following code example is from the <a href="wdf.sample_kmdf_drivers">AMCC5933</a> sample driver. This example shows an <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> callback function. The example notifies the framework that a DMA transfer has completed. If the framework indicates that this transfer is the last one for the DMA transaction, the code deletes the DMA transaction object and completes the associated I/O request.</p>

<p>Framework-based drivers must call one of the following methods whenever a <a href="wdf.dma_transactions_and_dma_transfers">DMA transfer</a> is complete:</p>

<p><b>WdfDmaTransactionDmaCompleted</b></p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547049">WdfDmaTransactionDmaCompletedFinal</a>
</p>

<p>Typically, drivers call these methods from within an <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> event callback function, after a device interrupt indicates the completion of a DMA transfer operation. A driver for a system-mode DMA device might call these methods from within an <a href="https://msdn.microsoft.com/C638A505-AAE1-48FC-B06B-F2F161ADC948">EvtDmaTransactionDmaTransferComplete</a> event callback function.</p>

<p>The framework might divide a <a href="wdf.dma_transactions_and_dma_transfers">DMA transaction</a> into several DMA transfer operations. Therefore, the driver must examine the method's return value to determine if additional transfers are required. </p>

<p>If the method returns <b>FALSE</b>, the <i>Status</i> location receives STATUS_MORE_PROCESSING_REQUIRED and additional DMA operations are required to complete the transaction. Typically, the <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> event callback function does nothing else at this point. Instead, the framework calls the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function, so the callback function can begin the next transfer. </p>

<p>If the method returns <b>TRUE</b>, no more transfers will occur for the specified transaction. In this case, a <i>Status</i> value of STATUS_SUCCESS means that the framework did not encounter any errors and the DMA transaction is complete. </p>

<p>If the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/hh439264">WdfDmaTransactionStopSystemTransfer</a> before calling <b>WdfDmaTransactionDmaCompleted</b>, <b>WdfDmaTransactionDmaCompleted</b> returns <b>TRUE</b> and a <i>Status</i> value of <b>STATUS_CANCELLED</b>.</p>

<p>For transactions that were set for <a href="https://msdn.microsoft.com/windows/hardware/drivers/wdf/">single transfer</a>, <b>WdfDmaTransactionDmaCompleted</b> returns <b>TRUE</b> and a <i>Status</i> value of <b>STATUS_WDF_TOO_MANY_TRANSFERS</b> if the hardware fails to complete the transaction in a single transfer, even though initialization succeeded.
 	This could happen for hardware that reports residual transfers for each DMA operation. For example, the driver programs the device to write 64KB, but the device writes only 60KB.
   In this case, the driver might repeat the DMA operation or reset the device.</p>

<p>Any other value for <i>Status</i> means that the framework detected an error and the DMA transaction might not have been completed.</p>

<p>When <b>WdfDmaTransactionDmaCompleted</b> returns <b>TRUE</b>, the driver typically does the following:</p>

<p>Calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff548734">WdfObjectDelete</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a> to delete or reuse the transaction object, respectively.</p>

<p>Completes the I/O request, if the DMA transaction is associated with an I/O request. (Drivers complete requests by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549945">WdfRequestComplete</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a>.)</p>

<p>For more information about completing DMA transfers, see <a href="NULL">Completing a DMA Transfer</a>.</p>

<p>The following code example is from the <a href="wdf.sample_kmdf_drivers">AMCC5933</a> sample driver. This example shows an <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> callback function. The example notifies the framework that a DMA transfer has completed. If the framework indicates that this transfer is the last one for the DMA transaction, the code deletes the DMA transaction object and completes the associated I/O request.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfdmatransaction.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (see <a href="wdf.framework_library_versioning">Framework Library Versioning</a>.)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547049">WdfDmaTransactionDmaCompletedFinal</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548734">WdfObjectDelete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549945">WdfRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDmaTransactionDmaCompleted method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
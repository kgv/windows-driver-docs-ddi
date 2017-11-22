---
UID: NF.wdfdmatransaction.WdfDmaTransactionExecute
title: WdfDmaTransactionExecute
author: windows-driver-content
description: The WdfDmaTransactionExecute method begins the execution of a specified DMA transaction.
old-location: wdf\wdfdmatransactionexecute.htm
ms.assetid: 8f52557f-b65d-479d-aab4-1e4f7298c8f9
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
req.alt-api: WdfDmaTransactionExecute
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
ms.keywords: WdfDmaTransactionExecute
req.iface: 
req.product: Windows 10 or later.
---

# WdfDmaTransactionExecute function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDmaTransactionExecute</b> method begins the execution of a specified DMA transaction. </p>


## -syntax

````
NTSTATUS WdfDmaTransactionExecute(
  _In_     WDFDMATRANSACTION DmaTransaction,
  _In_opt_ WDFCONTEXT        Context
);
````


## -parameters
<dl>

### -param <i>DmaTransaction</i> [in]

<dd>
<p>A handle to a DMA transaction object that the driver obtained from a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>.</p>
</dd>

### -param <i>Context</i> [in, optional]

<dd>
<p>Driver-defined context information. The framework passes the value specified for <i>Context</i>, which can be a pointer, to the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function. This parameter is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p><b>WdfDmaTransactionExecute</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, the method might return one of the following values.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>The driver previously called <a href="https://msdn.microsoft.com/library/windows/hardware/hh451190">WdfDmaTransactionSetImmediateExecution</a> and the resources needed for the request are unavailable.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547062">WdfDmaTransactionExecute</a> was not preceded by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547099">WdfDmaTransactionInitialize</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547107">WdfDmaTransactionInitializeUsingRequest</a>.</p><dl>
<dt><b>STATUS_WDF_BUSY</b></dt>
</dl><p>The device performs single-packet transfers, and the driver called <a href="https://msdn.microsoft.com/library/windows/hardware/ff547062">WdfDmaTransactionExecute</a> while another transaction was executing.</p><dl>
<dt><b>STATUS_WDF_TOO_FRAGMENTED</b></dt>
</dl><p>The number of scatter/gather elements that the operating system needed to handle the specified transfer size was greater than the value that the driver's call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547014">WdfDmaEnablerSetMaximumScatterGatherElements</a> specified. For more information, see the following Remarks section.</p>

<p> </p>

<p>This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>The <b>WdfDmaTransactionExecute</b> method initializes a transaction's scatter/gather list for the first <a href="wdf.dma_transactions_and_dma_transfers">DMA transfer</a> that is associated with the specified <a href="wdf.dma_transactions_and_dma_transfers">DMA transaction</a>. (For single-packet transfers, the scatter/gather list contains a single element.) Then, the method calls the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function, and the callback function can program the device to begin the transfer. </p>

<p>Framework-based drivers typically call <b>WdfDmaTransactionExecute</b> from within an <a href="wdf.request_handlers">I/O queue event callback function</a>. </p>

<p>After a driver has called <a href="https://msdn.microsoft.com/library/windows/hardware/ff547099">WdfDmaTransactionInitialize</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547107">WdfDmaTransactionInitializeUsingRequest</a> to initialize a DMA transaction, the driver must call <b>WdfDmaTransactionExecute</b> only once before <a href="wdf.completing_a_dma_transaction">completing the DMA transaction</a>. </p>

<p>
          If <b>WdfDmaTransactionInitialize<i>Xxx</i></b> returns success but <b>WdfDmaTransactionExecute</b> returns an error value, your driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a>.</p>

<p>In framework versions prior to 1.11, if the device performs single-packet transfers, the operating system can execute only one DMA transaction at a time. In this case, <b>WdfDmaTransactionExecute</b> returns STATUS_WDF_BUSY if another transaction is executing.</p>

<p>In framework versions 1.11 and later, if the driver uses DMA version 3 to perform single-packet transfers, the operating system can store multiple DMA transactions in an internal queue. In this case, the driver can call <b>WdfDmaTransactionExecute</b> while another transaction is executing. To select DMA version 3, set the <b>WdmDmaVersionOverride</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff551290">WDF_DMA_ENABLER_CONFIG</a> to 3.</p>

<p>If the device performs scatter/gather transfers, the operating system can execute multiple DMA transactions simultaneously. In this case, the driver can call <b>WdfDmaTransactionExecute</b> while another transaction is executing.</p>

<p>If the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a> to report a partial transfer, and if the driver had specified the DMA transaction's data buffer by using MDLs that it chained together (using the <b>Next</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554414">MDL</a> structure), <b>WdfDmaTransactionExecute</b> can return STATUS_WDF_TOO_FRAGMENTED because the framework might recalculate the number and size of fragments and might exceed the number of allowed fragments.</p>

<p>The <b>WdfDmaTransactionExecute</b> returns STATUS_SUCCESS if the transaction was successfully started. To determine if the framework successfully sent all of the transaction's transfers to the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> callback function, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547049">WdfDmaTransactionDmaCompletedFinal</a>.</p>

<p>If the value that the <i>Context</i> parameter supplies is a pointer or handle, the memory that it references must be accessible in the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function at IRQL = DISPATCH_LEVEL. You can use <a href="wdf.framework_object_context_space">framework object context</a> to meet this requirement.</p>

<p>The driver can call <b>WdfDmaTransactionExecute</b> in a non-blocking manner if it has previously called <a href="https://msdn.microsoft.com/library/windows/hardware/hh451190">WdfDmaTransactionSetImmediateExecution</a>.</p>

<p>For more information about DMA transactions, see <a href="wdf.starting_a_dma_transaction">Starting a DMA Transaction</a>.</p>

<p>The following code example is from the <a href="wdf.sample_kmdf_drivers">PCIDRV</a> sample driver. This example creates and initializes a DMA transfer and begins its execution.</p>

<p>The <b>WdfDmaTransactionExecute</b> method initializes a transaction's scatter/gather list for the first <a href="wdf.dma_transactions_and_dma_transfers">DMA transfer</a> that is associated with the specified <a href="wdf.dma_transactions_and_dma_transfers">DMA transaction</a>. (For single-packet transfers, the scatter/gather list contains a single element.) Then, the method calls the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function, and the callback function can program the device to begin the transfer. </p>

<p>Framework-based drivers typically call <b>WdfDmaTransactionExecute</b> from within an <a href="wdf.request_handlers">I/O queue event callback function</a>. </p>

<p>After a driver has called <a href="https://msdn.microsoft.com/library/windows/hardware/ff547099">WdfDmaTransactionInitialize</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547107">WdfDmaTransactionInitializeUsingRequest</a> to initialize a DMA transaction, the driver must call <b>WdfDmaTransactionExecute</b> only once before <a href="wdf.completing_a_dma_transaction">completing the DMA transaction</a>. </p>

<p>
          If <b>WdfDmaTransactionInitialize<i>Xxx</i></b> returns success but <b>WdfDmaTransactionExecute</b> returns an error value, your driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a>.</p>

<p>In framework versions prior to 1.11, if the device performs single-packet transfers, the operating system can execute only one DMA transaction at a time. In this case, <b>WdfDmaTransactionExecute</b> returns STATUS_WDF_BUSY if another transaction is executing.</p>

<p>In framework versions 1.11 and later, if the driver uses DMA version 3 to perform single-packet transfers, the operating system can store multiple DMA transactions in an internal queue. In this case, the driver can call <b>WdfDmaTransactionExecute</b> while another transaction is executing. To select DMA version 3, set the <b>WdmDmaVersionOverride</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff551290">WDF_DMA_ENABLER_CONFIG</a> to 3.</p>

<p>If the device performs scatter/gather transfers, the operating system can execute multiple DMA transactions simultaneously. In this case, the driver can call <b>WdfDmaTransactionExecute</b> while another transaction is executing.</p>

<p>If the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a> to report a partial transfer, and if the driver had specified the DMA transaction's data buffer by using MDLs that it chained together (using the <b>Next</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554414">MDL</a> structure), <b>WdfDmaTransactionExecute</b> can return STATUS_WDF_TOO_FRAGMENTED because the framework might recalculate the number and size of fragments and might exceed the number of allowed fragments.</p>

<p>The <b>WdfDmaTransactionExecute</b> returns STATUS_SUCCESS if the transaction was successfully started. To determine if the framework successfully sent all of the transaction's transfers to the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> callback function, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547049">WdfDmaTransactionDmaCompletedFinal</a>.</p>

<p>If the value that the <i>Context</i> parameter supplies is a pointer or handle, the memory that it references must be accessible in the driver's <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> event callback function at IRQL = DISPATCH_LEVEL. You can use <a href="wdf.framework_object_context_space">framework object context</a> to meet this requirement.</p>

<p>The driver can call <b>WdfDmaTransactionExecute</b> in a non-blocking manner if it has previously called <a href="https://msdn.microsoft.com/library/windows/hardware/hh451190">WdfDmaTransactionSetImmediateExecution</a>.</p>

<p>For more information about DMA transactions, see <a href="wdf.starting_a_dma_transaction">Starting a DMA Transaction</a>.</p>

<p>The following code example is from the <a href="wdf.sample_kmdf_drivers">PCIDRV</a> sample driver. This example creates and initializes a DMA transfer and begins its execution.</p>

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
<a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547014">WdfDmaEnablerSetMaximumScatterGatherElements</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547049">WdfDmaTransactionDmaCompletedFinal</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547099">WdfDmaTransactionInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547107">WdfDmaTransactionInitializeUsingRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451190">WdfDmaTransactionSetImmediateExecution</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDmaTransactionExecute method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
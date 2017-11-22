---
UID: NF.wdfdmatransaction.WdfDmaTransactionSetSingleTransferRequirement
title: WdfDmaTransactionSetSingleTransferRequirement
author: windows-driver-content
description: The WdfDmaTransactionSetSingleTransferRequirement method specifies that a DMA transaction must complete in a single transfer.
old-location: wdf\wdfdmatransactionsetsingletransferrequirement.htm
ms.assetid: 988c7e70-3b2a-4a0f-91cf-dfab3ea07f05
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
req.kmdf-ver: 1.19
req.umdf-ver: 
req.alt-api: WdfDmaTransactionSetSingleTransferRequirement
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfDmaTransactionSetSingleTransferRequirement
req.iface: 
req.product: Windows 10 or later.
---

# WdfDmaTransactionSetSingleTransferRequirement function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDmaTransactionSetSingleTransferRequirement</b> method specifies that a DMA transaction must complete in a single transfer.</p>


## -syntax

````
void WdfDmaTransactionSetSingleTransferRequirement(
  _In_ WDFDMATRANSACTION DmaTransaction,
  _In_ BOOLEAN           RequireSingleTransfer
);
````


## -parameters
<dl>

### -param <i>DmaTransaction</i> [in]

<dd>
<p>A handle to a DMA transaction object that the driver obtained from a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>.</p>
</dd>

### -param <i>RequireSingleTransfer</i> [in]

<dd>
<p>A Boolean value that, if <b>TRUE</b>, specifies that the DMA transaction requires a single transfer.</p>
</dd>
</dl>

## -returns
<p>This method does not return a value.</p>

## -remarks
<p>This method requests a single transfer for a single transaction only. When the transaction object is recycled with <a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a> and reinitialized, this setting resets, similar to other transaction-level properties such as immediate execution and maximum transfer length.</p>

<p>To request single transfer for all DMA transactions created with a given DMA enabler, specify  <b>WDF_DMA_ENABLER_CONFIG_REQUIRE_SINGLE_TRANSFER</b> in <a href="https://msdn.microsoft.com/library/windows/hardware/hh439491">WDF_DMA_ENABLER_CONFIG_FLAGS</a> when calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff546983">WdfDmaEnablerCreate</a>. This is equivalent to calling <b>WdfDmaTransactionSetSingleTransferRequirement</b> for each transaction object created with the DMA enabler.</p>

<p>The driver calls <b>WdfDmaTransactionSetSingleTransferRequirement</b> after creating or recycling the transaction object, but before initializing or executing it.  For more info, see <a href="https://msdn.microsoft.com/windows/hardware/drivers/wdf/">Using Single Transfer DMA</a>.</p>

<p><b>WdfDmaTransactionSetSingleTransferRequirement</b> requires DMA version 3.
 To select DMA version 3, set the <b>WdmDmaVersionOverride</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff551290">WDF_DMA_ENABLER_CONFIG</a> to 3.</p>

<p>This method requests a single transfer for a single transaction only. When the transaction object is recycled with <a href="https://msdn.microsoft.com/library/windows/hardware/ff547114">WdfDmaTransactionRelease</a> and reinitialized, this setting resets, similar to other transaction-level properties such as immediate execution and maximum transfer length.</p>

<p>To request single transfer for all DMA transactions created with a given DMA enabler, specify  <b>WDF_DMA_ENABLER_CONFIG_REQUIRE_SINGLE_TRANSFER</b> in <a href="https://msdn.microsoft.com/library/windows/hardware/hh439491">WDF_DMA_ENABLER_CONFIG_FLAGS</a> when calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff546983">WdfDmaEnablerCreate</a>. This is equivalent to calling <b>WdfDmaTransactionSetSingleTransferRequirement</b> for each transaction object created with the DMA enabler.</p>

<p>The driver calls <b>WdfDmaTransactionSetSingleTransferRequirement</b> after creating or recycling the transaction object, but before initializing or executing it.  For more info, see <a href="https://msdn.microsoft.com/windows/hardware/drivers/wdf/">Using Single Transfer DMA</a>.</p>

<p><b>WdfDmaTransactionSetSingleTransferRequirement</b> requires DMA version 3.
 To select DMA version 3, set the <b>WdmDmaVersionOverride</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff551290">WDF_DMA_ENABLER_CONFIG</a> to 3.</p>

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
<p>1.19</p>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547099">WdfDmaTransactionInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547107">WdfDmaTransactionInitializeUsingRequest</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDmaTransactionSetSingleTransferRequirement method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
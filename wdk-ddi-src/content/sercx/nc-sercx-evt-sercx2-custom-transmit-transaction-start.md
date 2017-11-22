---
UID: NC.sercx.EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START
title: EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START
author: windows-driver-content
description: The EvtSerCx2CustomTransmitTransactionStart event callback function is called by version 2 of the serial framework extension (SerCx2) to start a custom-transmit transaction.
old-location: serports\evtsercx2customtransmittransactionstart.htm
ms.assetid: BFB2DBBE-9E00-4C1D-B336-2B9C48E98DD3
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: serports
req.header: sercx.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Available starting with Windows 8.1.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: EvtSerCx2CustomTransmitTransactionStart
req.alt-loc: 2.0\Sercx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Called at IRQL <= DISPATCH_LEVEL.
ms.keywords: SENSOR_VALUE_PAIR, SENSOR_VALUE_PAIR, *PSENSOR_VALUE_PAIR
req.iface: 
req.product: Windows 10 or later.
---

# EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START callback



## -description
<p>The <i>EvtSerCx2CustomTransmitTransactionStart</i> event callback function is called by version 2 of the serial framework extension (SerCx2) to start a custom-transmit transaction.</p>


## -prototype

````
EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START EvtSerCx2CustomTransmitTransactionStart;

VOID EvtSerCx2CustomTransmitTransactionStart(
  _In_ SERCX2CUSTOMTRANSMITTRANSACTION CustomTransmitTransaction,
  _In_ WDFREQUEST                      Request,
  _In_ PMDL                            Mdl,
  _In_ ULONG                           Offset,
  _In_ ULONG                           Length
)
{ ... }
````


## -parameters
<dl>

### -param <i>CustomTransmitTransaction</i> [in]

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/dn265257">SERCX2CUSTOMTRANSMITTRANSACTION</a> handle to a custom-transmit-transaction object. The serial controller driver previously called the <a href="https://msdn.microsoft.com/library/windows/hardware/dn265259">SerCx2CustomTransmitTransactionCreate</a> method to create this object.</p>
</dd>

### -param <i>Request</i> [in]

<dd>
<p>A handle to the framework request object associated with the custom-transmit transaction. The driver is responsible for completing this request. This request might not be the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550819">IRP_MJ_WRITE</a> request sent by the client, and thus the serial controller driver should not try to use this request to access the write buffer. This request is primarily used for cancellation, completion, and queue forwarding (if needed). To access the write buffer for the client's write request, use the <i>Mdl</i>, <i>Offset</i>, and <i>Length</i> parameters.</p>
</dd>

### -param <i>Mdl</i> [in]

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff554414">MDL</a> that describes the memory pages that are spanned by the write buffer for the custom-transmit transaction. The scatter/gather list for the DMA transfer will use the region of this memory that is specified by the <i>Offset</i> and <i>Length</i> parameters. For more information about MDL chains, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565421">Using MDLs</a>.</p>
</dd>

### -param <i>Offset</i> [in]

<dd>
<p>The starting offset for the data transfer. This parameter is a byte offset from the start of the buffer region described by the MDL. If the MDL specifies a total of N bytes of buffer space, possible values of <i>Offset</i> are in the range 0 to N–1.</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>The size, in bytes, of the data transfer. If the MDL specifies a total of N bytes of buffer space, possible values of <i>Length</i> are in the range 1 to N–<i>Offset</i>.</p>
</dd>
</dl>

## -returns
<p>None.</p>

## -remarks
<p>Your serial controller driver must implement this function if it creates a custom-transmit-transaction object. If implemented, the driver registers the function in the <a href="https://msdn.microsoft.com/library/windows/hardware/dn265259">SerCx2CustomTransmitTransactionCreate</a> call that creates this object.</p>

<p>After SerCx2 calls the <i>EvtSerCx2CustomTransmitTransactionStart</i> function, the serial controller driver initiates the transaction by programming the custom data-transfer mechanism to move data from the buffer in the write request to the transmit FIFO in the serial controller hardware. Unless the request can be completed immediately, before the <i>EvtSerCx2CustomTransmitTransactionStart</i> function returns, the driver must call a method such as <a href="https://msdn.microsoft.com/library/windows/hardware/ff549984">WdfRequestMarkCancelableEx</a> to mark the request as cancelable.</p>

<p>After the transaction finishes and the driver completes the pending write request, SerCx2 calls the <a href="https://msdn.microsoft.com/CEADF06B-FD60-4B4C-AB59-1ED6B1226204">EvtSerCx2CustomTransmitTransactionCleanup</a> event callback function, if the driver implements this function.</p>

<p>If the serial controller driver implements an <a href="https://msdn.microsoft.com/CFC577D6-747F-4752-8CB6-7410C21487B6">EvtSerCx2CustomTransmitTransactionInitialize</a> event callback function, SerCx2 calls this function before calling the <i>EvtSerCx2CustomTransmitTransactionStart</i> function. Just before the <i>EvtSerCx2CustomTransmitTransactionStart</i> call, and after the <i>EvtSerCx2CustomTransmitTransactionInitialize</i> call returns, SerCx2 starts the timer that detects whether the write request times out. For more information, see the discussion of total time-outs in <a href="https://msdn.microsoft.com/library/windows/hardware/hh439614">SERIAL_TIMEOUTS</a>.</p>

<p>The serial controller driver should complete the pending write request only after the last byte in the transmit FIFO has been transmitted to the serially connected peripheral device. There can be no guarantee that data written to the transmit FIFO will be transmitted without a significant delay, and a serial controller driver that assumes that such a guarantee exists can cause reliability problems for peripheral drivers.</p>

<p>If the custom data-transfer mechanism is a bus-master DMA device, the <i>EvtSerCx2CustomTransmitTransactionStart</i> function can call a method such as <a href="https://msdn.microsoft.com/library/windows/hardware/hh451182">WdfDmaTransactionInitializeUsingOffset</a> to initiate a DMA transaction that uses the write buffer described by the <i>Mdl</i>, <i>Offset</i>, and <i>Length</i> parameters.</p>

<p>For more information about the <i>Mdl</i>, <i>Offset</i>, and <i>Length</i> parameters, see Remarks in <a href="https://msdn.microsoft.com/CFC577D6-747F-4752-8CB6-7410C21487B6">EvtSerCx2CustomTransmitTransactionInitialize</a>.</p>

<p>If the request object identified by the <i>Request</i> parameter contains storage for a private context, this storage might be uninitialized the first time the serial controller driver accesses the context. On first access, the driver typically should fill the context with zeros, and then, if needed, explicitly set any fields in the context that require nonzero initial values.</p>

<p>For more information, see <a href="NULL">SerCx2 Custom-Transmit Transactions</a>.</p>

<p>To define an <i>EvtSerCx2CustomTransmitTransactionStart</i> callback function, you must first provide a function declaration that identifies the type of callback function you're defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtSerCx2CustomTransmitTransactionStart</i> callback function that is named <code>MyCustomTransmitTransactionStart</code>, use the <b>EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START</b> function type, as shown in this code example:</p>

<p>Then, implement your callback function as follows:</p>

<p>The <b>EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START</b> function type is defined in the Sercx.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For more information about _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?LinkId=286697">Annotating Function Behavior</a>.</p>

<p>Your serial controller driver must implement this function if it creates a custom-transmit-transaction object. If implemented, the driver registers the function in the <a href="https://msdn.microsoft.com/library/windows/hardware/dn265259">SerCx2CustomTransmitTransactionCreate</a> call that creates this object.</p>

<p>After SerCx2 calls the <i>EvtSerCx2CustomTransmitTransactionStart</i> function, the serial controller driver initiates the transaction by programming the custom data-transfer mechanism to move data from the buffer in the write request to the transmit FIFO in the serial controller hardware. Unless the request can be completed immediately, before the <i>EvtSerCx2CustomTransmitTransactionStart</i> function returns, the driver must call a method such as <a href="https://msdn.microsoft.com/library/windows/hardware/ff549984">WdfRequestMarkCancelableEx</a> to mark the request as cancelable.</p>

<p>After the transaction finishes and the driver completes the pending write request, SerCx2 calls the <a href="https://msdn.microsoft.com/CEADF06B-FD60-4B4C-AB59-1ED6B1226204">EvtSerCx2CustomTransmitTransactionCleanup</a> event callback function, if the driver implements this function.</p>

<p>If the serial controller driver implements an <a href="https://msdn.microsoft.com/CFC577D6-747F-4752-8CB6-7410C21487B6">EvtSerCx2CustomTransmitTransactionInitialize</a> event callback function, SerCx2 calls this function before calling the <i>EvtSerCx2CustomTransmitTransactionStart</i> function. Just before the <i>EvtSerCx2CustomTransmitTransactionStart</i> call, and after the <i>EvtSerCx2CustomTransmitTransactionInitialize</i> call returns, SerCx2 starts the timer that detects whether the write request times out. For more information, see the discussion of total time-outs in <a href="https://msdn.microsoft.com/library/windows/hardware/hh439614">SERIAL_TIMEOUTS</a>.</p>

<p>The serial controller driver should complete the pending write request only after the last byte in the transmit FIFO has been transmitted to the serially connected peripheral device. There can be no guarantee that data written to the transmit FIFO will be transmitted without a significant delay, and a serial controller driver that assumes that such a guarantee exists can cause reliability problems for peripheral drivers.</p>

<p>If the custom data-transfer mechanism is a bus-master DMA device, the <i>EvtSerCx2CustomTransmitTransactionStart</i> function can call a method such as <a href="https://msdn.microsoft.com/library/windows/hardware/hh451182">WdfDmaTransactionInitializeUsingOffset</a> to initiate a DMA transaction that uses the write buffer described by the <i>Mdl</i>, <i>Offset</i>, and <i>Length</i> parameters.</p>

<p>For more information about the <i>Mdl</i>, <i>Offset</i>, and <i>Length</i> parameters, see Remarks in <a href="https://msdn.microsoft.com/CFC577D6-747F-4752-8CB6-7410C21487B6">EvtSerCx2CustomTransmitTransactionInitialize</a>.</p>

<p>If the request object identified by the <i>Request</i> parameter contains storage for a private context, this storage might be uninitialized the first time the serial controller driver accesses the context. On first access, the driver typically should fill the context with zeros, and then, if needed, explicitly set any fields in the context that require nonzero initial values.</p>

<p>For more information, see <a href="NULL">SerCx2 Custom-Transmit Transactions</a>.</p>

<p>To define an <i>EvtSerCx2CustomTransmitTransactionStart</i> callback function, you must first provide a function declaration that identifies the type of callback function you're defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtSerCx2CustomTransmitTransactionStart</i> callback function that is named <code>MyCustomTransmitTransactionStart</code>, use the <b>EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START</b> function type, as shown in this code example:</p>

<p>Then, implement your callback function as follows:</p>

<p>The <b>EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START</b> function type is defined in the Sercx.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For more information about _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?LinkId=286697">Annotating Function Behavior</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8.1.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>2.0\Sercx.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Called at IRQL &lt;= DISPATCH_LEVEL.</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/CEADF06B-FD60-4B4C-AB59-1ED6B1226204">EvtSerCx2CustomTransmitTransactionCleanup</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/CFC577D6-747F-4752-8CB6-7410C21487B6">EvtSerCx2CustomTransmitTransactionInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550819">IRP_MJ_WRITE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554414">MDL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn265257">SERCX2CUSTOMTRANSMITTRANSACTION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn265259">SerCx2CustomTransmitTransactionCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439614">SERIAL_TIMEOUTS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451182">WdfDmaTransactionInitializeUsingOffset</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549984">WdfRequestMarkCancelableEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [serports\serports]:%20EVT_SERCX2_CUSTOM_TRANSMIT_TRANSACTION_START callback function%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
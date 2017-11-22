---
UID: NF.wdfusb.WdfUsbTargetPipeFormatRequestForRead
title: WdfUsbTargetPipeFormatRequestForRead
author: windows-driver-content
description: The WdfUsbTargetPipeFormatRequestForRead method builds a read request for a USB input pipe, but it does not send the request.
old-location: wdf\wdfusbtargetpipeformatrequestforread.htm
ms.assetid: 33a6f597-2f33-4214-80c1-8bded182800a
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfusb.h
req.include-header: Wdfusb.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfUsbTargetPipeFormatRequestForRead
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2, RequestFormattedValid, RequestSendAndForgetNoFormatting, RequestSendAndForgetNoFormatting2, UsbKmdfIrql, UsbKmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfUsbTargetPipeFormatRequestForRead
req.iface: 
req.product: Windows 10 or later.
---

# WdfUsbTargetPipeFormatRequestForRead function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfUsbTargetPipeFormatRequestForRead</b> method builds a read request for a USB input pipe, but it does not send the request.</p>


## -syntax

````
NTSTATUS WdfUsbTargetPipeFormatRequestForRead(
  _In_     WDFUSBPIPE        Pipe,
  _In_     WDFREQUEST        Request,
  _In_opt_ WDFMEMORY         ReadMemory,
  _In_opt_ PWDFMEMORY_OFFSET ReadOffset
);
````


## -parameters
<dl>

### -param <i>Pipe</i> [in]

<dd>
<p>A handle to a framework pipe object that was obtained by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550057">WdfUsbInterfaceGetConfiguredPipe</a>. </p>
</dd>

### -param <i>Request</i> [in]

<dd>
<p>A handle to a framework request object. For more information, see the following Remarks section.</p>
</dd>

### -param <i>ReadMemory</i> [in, optional]

<dd>
<p>A handle to a framework memory object. This object represents a buffer that will receive data from the pipe. The buffer size must be a multiple of the pipe's maximum packet size unless the driver has called <a href="https://msdn.microsoft.com/library/windows/hardware/ff551160">WdfUsbTargetPipeSetNoMaximumPacketSizeCheck</a>. For more information about this buffer, see the following Remarks section.</p>
</dd>

### -param <i>ReadOffset</i> [in, optional]

<dd>
<p>A pointer to a caller-allocated <a href="https://msdn.microsoft.com/library/windows/hardware/ff561398">WDFMEMORY_OFFSET</a> structure that supplies optional byte offset and length values. The framework uses these values to determine the beginning address and length, within the read buffer, for the data transfer. If this pointer is <b>NULL</b>, the data transfer begins at the beginning of the buffer, and the transfer size is the buffer size.</p>
</dd>
</dl>

## -returns
<p><b>WdfUsbTargetPipeFormatRequestForRead</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method can return one of the following values:</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid parameter was detected.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>Insufficient memory was available.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>An invalid memory descriptor was specified, the pipe's type was not valid, the transfer direction was invalid, or the specified I/O request was already queued to an I/O target.</p><dl>
<dt><b>STATUS_INTEGER_OVERFLOW</b></dt>
</dl><p>The offset that the <i>Offset</i> parameter specified was invalid.</p><dl>
<dt><b>STATUS_INVALID_BUFFER_SIZE</b></dt>
</dl><p>The buffer size was not a multiple of the pipe's maximum packet size. The buffer size must be a multiple of the pipe's maximum packet size unless the driver has called <a href="https://msdn.microsoft.com/library/windows/hardware/ff551160">WdfUsbTargetPipeSetNoMaximumPacketSizeCheck</a>.</p><dl>
<dt><b>STATUS_REQUEST_NOT_ACCEPTED</b></dt>
</dl><p>The I/O request packet (<a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>) that the <i>Request</i> parameter represents does not provide enough <a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a> structures to allow the driver to forward the request.</p>

<p> </p>

<p>This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>Use <b>WdfUsbTargetPipeFormatRequestForRead</b>, followed by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>, to send read requests either synchronously or asynchronously. Alternatively, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551155">WdfUsbTargetPipeReadSynchronously</a> method to send read requests synchronously. </p>

<p>The pipe that the <i>Pipe</i> parameter specifies must be an input pipe, and the pipe's <a href="https://msdn.microsoft.com/library/windows/hardware/hh439450">type</a> must be <b>WdfUsbPipeTypeBulk</b> or <b>WdfUsbPipeTypeInterrupt</b>.</p>

<p>You can forward an I/O request that your driver received in an I/O queue, or you can create and send a new request. In either case, the framework requires a request object and some buffer space.</p>

<p>To forward an I/O request that your driver received in an I/O queue:</p>

<p>Specify the received request's handle for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>Request</i> parameter.</p>

<p>Use the received request's output buffer for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>ReadMemory</i> parameter.</p>

<p>The driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550019">WdfRequestRetrieveOutputMemory</a> to obtain a handle to a framework memory object that represents the request's output buffer, and use that handle as the value for the <i>ReadMemory</i> parameter.</p>

<p>For more information about forwarding an I/O request, see <a href="wdf.forwarding_i_o_requests">Forwarding I/O Requests</a>.</p>

<p>Drivers often divide received I/O requests into smaller requests that they send to an I/O target, so your driver might create new requests.</p>

<p>To create a new I/O request:</p>

<p>Create a new request object and supply its handle for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>Request</i> parameter.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> to preallocate one or more request objects. You can reuse these request objects by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>. Your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function can preallocate request objects for a device.</p>

<p>Provide buffer space, and supply the buffer's handle for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>ReadMemory</i> parameter. </p>

<p>Your driver must specify this buffer space as a WDFMEMORY handle to framework-managed memory. Your driver can do either of the following:</p>

<p>Note that if your driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550019">WdfRequestRetrieveOutputMemory</a> and passes the memory handle to <b>WdfUsbTargetPipeFormatRequestForRead</b>, the driver must not complete the received I/O request until after the driver deletes, reuses, or reformats the new, driver-created request object. (<b>WdfUsbTargetPipeFormatRequestForRead</b> increments the memory object's reference count. Deleting, reusing, or reformatting a request object decrements the memory object's reference count.)</p>

<p>After calling <b>WdfUsbTargetPipeFormatRequestForRead</b> to format an I/O request, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a> to send the request (either synchronously or asynchronously) to an I/O target.</p>

<p>Multiple calls to <b>WdfUsbTargetPipeFormatRequestForRead</b> that use the same request do not cause additional resource allocations. Therefore, to reduce the chance that <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> will return STATUS_INSUFFICIENT_RESOURCES, your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function can call <b>WdfRequestCreate</b> to preallocate one or more request objects for a device. The driver can subsequently reuse (call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>), reformat (call <b>WdfUsbTargetPipeFormatRequestForRead</b>), and resend (call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>) each request object without risking a STATUS_INSUFFICIENT_RESOURCES return value from a later call to <b>WdfRequestCreate</b>. All subsequent calls to <b>WdfUsbTargetPipeFormatRequestForRead</b> for the reused request object will return STATUS_SUCCESS, if parameter values do not change. (If the driver does not call the same request-formatting method each time, additional resources might be allocated.)</p>

<p>The framework sets the USBD_SHORT_TRANSFER_OK flag in its internal  <a href="https://msdn.microsoft.com/library/windows/hardware/ff538923">URB</a>. Setting this flag allows the last packet of a data transfer to be less than the maximum packet size.</p>

<p>For information about obtaining status information after an I/O request completes, see <a href="wdf.completing_i_o_requests#obtaining_completion_information#obtaining_completion_information">Obtaining Completion Information</a>.</p>

<p>For more information about the <b>WdfUsbTargetPipeFormatRequestForRead</b> method and USB I/O targets, see <a href="wdf.usb_i_o_targets">USB I/O Targets</a>.</p>

<p>The following code example is from the <a href="http://go.microsoft.com/fwlink/p/?linkid=256131">kmdf_fx2</a> sample driver. This example is an <a href="https://msdn.microsoft.com/d6fbb153-1355-4e94-b5d3-a218bd8c565d">EvtIoRead</a> callback function that forwards a read request to a USB pipe. The example calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550019">WdfRequestRetrieveOutputMemory</a> to obtain the request's output buffer, and then it formats the read request so that the request can be sent to a USB pipe. Next, the example registers a <a href="https://msdn.microsoft.com/7d3eb4d6-9fc7-4924-9b95-f5824713049b">CompletionRoutine</a> callback function. Finally, it sends the request to the USB pipe.</p>

<p>Use <b>WdfUsbTargetPipeFormatRequestForRead</b>, followed by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>, to send read requests either synchronously or asynchronously. Alternatively, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551155">WdfUsbTargetPipeReadSynchronously</a> method to send read requests synchronously. </p>

<p>The pipe that the <i>Pipe</i> parameter specifies must be an input pipe, and the pipe's <a href="https://msdn.microsoft.com/library/windows/hardware/hh439450">type</a> must be <b>WdfUsbPipeTypeBulk</b> or <b>WdfUsbPipeTypeInterrupt</b>.</p>

<p>You can forward an I/O request that your driver received in an I/O queue, or you can create and send a new request. In either case, the framework requires a request object and some buffer space.</p>

<p>To forward an I/O request that your driver received in an I/O queue:</p>

<p>Specify the received request's handle for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>Request</i> parameter.</p>

<p>Use the received request's output buffer for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>ReadMemory</i> parameter.</p>

<p>The driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550019">WdfRequestRetrieveOutputMemory</a> to obtain a handle to a framework memory object that represents the request's output buffer, and use that handle as the value for the <i>ReadMemory</i> parameter.</p>

<p>For more information about forwarding an I/O request, see <a href="wdf.forwarding_i_o_requests">Forwarding I/O Requests</a>.</p>

<p>Drivers often divide received I/O requests into smaller requests that they send to an I/O target, so your driver might create new requests.</p>

<p>To create a new I/O request:</p>

<p>Create a new request object and supply its handle for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>Request</i> parameter.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> to preallocate one or more request objects. You can reuse these request objects by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>. Your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function can preallocate request objects for a device.</p>

<p>Provide buffer space, and supply the buffer's handle for the <b>WdfUsbTargetPipeFormatRequestForRead</b> method's <i>ReadMemory</i> parameter. </p>

<p>Your driver must specify this buffer space as a WDFMEMORY handle to framework-managed memory. Your driver can do either of the following:</p>

<p>Note that if your driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550019">WdfRequestRetrieveOutputMemory</a> and passes the memory handle to <b>WdfUsbTargetPipeFormatRequestForRead</b>, the driver must not complete the received I/O request until after the driver deletes, reuses, or reformats the new, driver-created request object. (<b>WdfUsbTargetPipeFormatRequestForRead</b> increments the memory object's reference count. Deleting, reusing, or reformatting a request object decrements the memory object's reference count.)</p>

<p>After calling <b>WdfUsbTargetPipeFormatRequestForRead</b> to format an I/O request, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a> to send the request (either synchronously or asynchronously) to an I/O target.</p>

<p>Multiple calls to <b>WdfUsbTargetPipeFormatRequestForRead</b> that use the same request do not cause additional resource allocations. Therefore, to reduce the chance that <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> will return STATUS_INSUFFICIENT_RESOURCES, your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function can call <b>WdfRequestCreate</b> to preallocate one or more request objects for a device. The driver can subsequently reuse (call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>), reformat (call <b>WdfUsbTargetPipeFormatRequestForRead</b>), and resend (call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>) each request object without risking a STATUS_INSUFFICIENT_RESOURCES return value from a later call to <b>WdfRequestCreate</b>. All subsequent calls to <b>WdfUsbTargetPipeFormatRequestForRead</b> for the reused request object will return STATUS_SUCCESS, if parameter values do not change. (If the driver does not call the same request-formatting method each time, additional resources might be allocated.)</p>

<p>The framework sets the USBD_SHORT_TRANSFER_OK flag in its internal  <a href="https://msdn.microsoft.com/library/windows/hardware/ff538923">URB</a>. Setting this flag allows the last packet of a data transfer to be less than the maximum packet size.</p>

<p>For information about obtaining status information after an I/O request completes, see <a href="wdf.completing_i_o_requests#obtaining_completion_information#obtaining_completion_information">Obtaining Completion Information</a>.</p>

<p>For more information about the <b>WdfUsbTargetPipeFormatRequestForRead</b> method and USB I/O targets, see <a href="wdf.usb_i_o_targets">USB I/O Targets</a>.</p>

<p>The following code example is from the <a href="http://go.microsoft.com/fwlink/p/?linkid=256131">kmdf_fx2</a> sample driver. This example is an <a href="https://msdn.microsoft.com/d6fbb153-1355-4e94-b5d3-a218bd8c565d">EvtIoRead</a> callback function that forwards a read request to a USB pipe. The example calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550019">WdfRequestRetrieveOutputMemory</a> to obtain the request's output buffer, and then it formats the read request so that the request can be sent to a USB pipe. Next, the example registers a <a href="https://msdn.microsoft.com/7d3eb4d6-9fc7-4924-9b95-f5824713049b">CompletionRoutine</a> callback function. Finally, it sends the request to the USB pipe.</p>

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
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfusb.h (include Wdfusb.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.dll (UMDF)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551618">RequestFormattedValid</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/jj126209">RequestSendAndForgetNoFormatting</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/jj126210">RequestSendAndForgetNoFormatting2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff554042">UsbKmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh995019">UsbKmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561398">WDFMEMORY_OFFSET</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549974">WdfRequestGetStatus</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550030">WdfRequestSetCompletionRoutine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550057">WdfUsbInterfaceGetConfiguredPipe</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfUsbTargetPipeFormatRequestForRead method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
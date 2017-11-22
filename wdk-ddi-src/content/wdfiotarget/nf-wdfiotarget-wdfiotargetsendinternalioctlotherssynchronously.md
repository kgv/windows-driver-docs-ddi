---
UID: NF.wdfiotarget.WdfIoTargetSendInternalIoctlOthersSynchronously
title: WdfIoTargetSendInternalIoctlOthersSynchronously
author: windows-driver-content
description: The WdfIoTargetSendInternalIoctlOthersSynchronously method builds a non-standard internal device control request and sends it synchronously to an I/O target.
old-location: wdf\wdfiotargetsendinternalioctlotherssynchronously.htm
ms.assetid: 53070b37-3836-49c2-91d1-369552afe214
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfiotarget.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfIoTargetSendInternalIoctlOthersSynchronously
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DeferredRequestCompleted, DriverCreate, IoctlReqs, KmdfIrql, KmdfIrql2, ReadReqs, RequestCompleted, RequestCompletedLocal, WriteReqs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfIoTargetSendInternalIoctlOthersSynchronously
req.iface: 
req.product: Windows 10 or later.
---

# WdfIoTargetSendInternalIoctlOthersSynchronously function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method builds a non-standard internal device control request and sends it synchronously to an I/O target.</p>


## -syntax

````
NTSTATUS WdfIoTargetSendInternalIoctlOthersSynchronously(
  _In_      WDFIOTARGET               IoTarget,
  _In_opt_  WDFREQUEST                Request,
  _In_      ULONG                     IoctlCode,
  _In_opt_  PWDF_MEMORY_DESCRIPTOR    OtherArg1,
  _In_opt_  PWDF_MEMORY_DESCRIPTOR    OtherArg2,
  _In_opt_  PWDF_MEMORY_DESCRIPTOR    OtherArg4,
  _In_opt_  PWDF_REQUEST_SEND_OPTIONS RequestOptions,
  _Out_opt_ PULONG_PTR                BytesReturned
);
````


## -parameters
<dl>

### -param <i>IoTarget</i> [in]

<dd>
<p>A handle to a local or remote I/O target object that was obtained from a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff546017">WdfDeviceGetIoTarget</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548591">WdfIoTargetCreate</a>, or from a method that a specialized I/O target supplies.</p>
</dd>

### -param <i>Request</i> [in, optional]

<dd>
<p>A handle to a framework request object. This parameter is optional and can be <b>NULL</b>. For more information, see the following Remarks section.</p>
</dd>

### -param <i>IoctlCode</i> [in]

<dd>
<p>An I/O control code (IOCTL) that the I/O target supports. </p>
</dd>

### -param <i>OtherArg1</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552392">WDF_MEMORY_DESCRIPTOR</a> structure that describes a memory buffer that contains context information. This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>OtherArg2</i> [in, optional]

<dd>
<p>A pointer to a WDF_MEMORY_DESCRIPTOR structure that describes a memory buffer that contains context information. This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>OtherArg4</i> [in, optional]

<dd>
<p>A pointer to a WDF_MEMORY_DESCRIPTOR structure that describes a memory buffer that contains context information. This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>RequestOptions</i> [in, optional]

<dd>
<p>A pointer to a caller-allocated <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure that specifies options for the request. This pointer is optional and can be <b>NULL</b>. For more information, see the following Remarks section.</p>
</dd>

### -param <i>BytesReturned</i> [out, optional]

<dd>
<p>A pointer to a location that receives information (such as the number of bytes that were transferred) that another driver supplies when it completes the request by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a>. This pointer is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> returns after the internal device control request completes, and the return value is the request's completion status value. Otherwise, this method might return one of the following values:</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid parameter was detected.</p><dl>
<dt><b>STATUS_INFO_LENGTH_MISMATCH</b></dt>
</dl><p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure that the <i>RequestOptions</i> parameter pointed to was incorrect.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The request was already queued to an I/O target.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>The framework could not allocate system resources (typically memory).</p><dl>
<dt><b>STATUS_IO_TIMEOUT</b></dt>
</dl><p>The driver supplied a time-out value and the request did not complete within the allotted time.</p><dl>
<dt><b>STATUS_REQUEST_NOT_ACCEPTED</b></dt>
</dl><p>The I/O request packet (<a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>) that the <i>Request</i> parameter represents does not provide enough <a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a> structures to allow the driver to forward the request.</p>

<p> </p>

<p>This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>A non-standard internal device control request uses an IOCTL code to identify the operation to be performed, but the request does not use the standard input and output buffers that other internal device control requests use. If you are creating a set of interacting drivers, you can define how this set of drivers use the request's arguments: <i>OtherArg1</i>, <i>OtherArg2</i>, and <i>OtherArg4</i>. </p>

<p>There is no parameter called <i>OtherArg3</i> because the framework associates these parameters with the <b>Argument1</b>, <b>Argument2</b>, and <b>Argument4</b> members of the <b>Other.Parameters</b> union in the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a> structure. The <b>Argument3</b> member in that union receives the value from the <i>IoctlCode</i> parameter, so it is  not available for other driver-supplied values.</p>

<p>Use the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method to send non-standard internal device control requests synchronously. To send internal device control requests asynchronously, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff548599">WdfIoTargetFormatRequestForInternalIoctlOthers</a>, followed by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>. </p>

<p>For more information about internal device control requests, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565406">Using I/O Control Codes</a>.</p>

<p>The <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method does not return until the request has completed, unless the driver supplies a time-out value in the <i>RequestOptions</i> parameter's <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure, or unless an error is detected.</p>

<p>You can forward a non-standard internal device control request that your driver received in an I/O queue, or you can create and send a new request. In either case, the framework requires a request object and possibly some context space.</p>

<p>To forward a non-standard internal device control request that your driver received in an I/O queue:</p>

<p>Specify the received request's handle for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>Request</i> parameter.</p>

<p>Use the received request's context information for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>OtherArg1</i>,<i>OtherArg2</i>, and<i>OtherArg4</i> parameters.</p>

<p>To obtain these parameter values, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549969">WdfRequestGetParameters</a> and use the <b>DeviceIoControl</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552472">WDF_REQUEST_PARAMETERS</a> structure that is returned. </p>

<p>For more information about forwarding an I/O request, see <a href="wdf.forwarding_i_o_requests">Forwarding I/O Requests</a>.</p>

<p>Drivers often divide received I/O requests into smaller requests that they send to an I/O target, so your driver might create new requests.</p>

<p>To create a new I/O request:</p>

<p>Supply a <b>NULL</b> request handle for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>Request</i> parameter, or create a new request object and supply its handle:<ul>
<li>If you supply a <b>NULL</b> request handle, the framework uses an internal request object. This technique is simple to use, but the driver cannot cancel the request.</li>
<li>If you call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> to create one or more request objects, you can reuse these request objects by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>. This technique enables your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function to preallocate request objects for a device. Additionally, another driver thread can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549941">WdfRequestCancelSentRequest</a> to cancel the request, if necessary.</li>
</ul>
</p>

<p>Your driver can specify a non-<b>NULL</b> <i>RequestOptions</i> parameter, whether the driver provides a non-<b>NULL</b> or a <b>NULL</b> <i>Request</i> parameter. You can, for example, use the <i>RequestOptions</i> parameter to specify a time-out value. </p>

<p>Provide context space for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>OtherArg1</i>,<i>OtherArg2</i>, and <i>OtherArg4</i> parameters, if the request requires them.</p>

<p>Your driver can specify this context space as locally allocated buffers, as WDFMEMORY handles, or as memory descriptor lists (MDLs). You can use whichever method is most convenient. </p>

<p>The following techniques to specify buffer space are available:</p>

<p>Supply local buffers.</p>

<p>Because <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> handles I/O requests synchronously, the driver can create request buffers that are local to the calling routine, as the following code example shows.</p>

<p>Supply WDFMEMORY handles.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548706">WdfMemoryCreate</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548712">WdfMemoryCreatePreallocated</a> to obtain a handle to framework-managed memory, as the following code example shows. </p>

<p>Supply MDLs.</p>

<p>Drivers can obtain MDLs that are associated with a received I/O request by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550016">WdfRequestRetrieveInputWdmMdl</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff550021">WdfRequestRetrieveOutputWdmMdl</a>.</p>

<p>For information about obtaining status information after an I/O request completes, see <a href="wdf.completing_i_o_requests#obtaining_completion_information#obtaining_completion_information">Obtaining Completion Information</a>.</p>

<p>For more information about <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b>, see <a href="wdf.sending_i_o_requests_to_general_i_o_targets">Sending I/O Requests to General I/O Targets</a>.</p>

<p>For more information about I/O targets, see <a href="wdf.using_i_o_targets">Using I/O Targets</a>.</p>

<p>The following code example initializes an IEEE 1394 IRB structure, uses the structure's address to initialize a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552392">WDF_MEMORY_DESCRIPTOR</a> structure, and then calls <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b>. </p>

<p>A non-standard internal device control request uses an IOCTL code to identify the operation to be performed, but the request does not use the standard input and output buffers that other internal device control requests use. If you are creating a set of interacting drivers, you can define how this set of drivers use the request's arguments: <i>OtherArg1</i>, <i>OtherArg2</i>, and <i>OtherArg4</i>. </p>

<p>There is no parameter called <i>OtherArg3</i> because the framework associates these parameters with the <b>Argument1</b>, <b>Argument2</b>, and <b>Argument4</b> members of the <b>Other.Parameters</b> union in the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a> structure. The <b>Argument3</b> member in that union receives the value from the <i>IoctlCode</i> parameter, so it is  not available for other driver-supplied values.</p>

<p>Use the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method to send non-standard internal device control requests synchronously. To send internal device control requests asynchronously, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff548599">WdfIoTargetFormatRequestForInternalIoctlOthers</a>, followed by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>. </p>

<p>For more information about internal device control requests, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565406">Using I/O Control Codes</a>.</p>

<p>The <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method does not return until the request has completed, unless the driver supplies a time-out value in the <i>RequestOptions</i> parameter's <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure, or unless an error is detected.</p>

<p>You can forward a non-standard internal device control request that your driver received in an I/O queue, or you can create and send a new request. In either case, the framework requires a request object and possibly some context space.</p>

<p>To forward a non-standard internal device control request that your driver received in an I/O queue:</p>

<p>Specify the received request's handle for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>Request</i> parameter.</p>

<p>Use the received request's context information for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>OtherArg1</i>,<i>OtherArg2</i>, and<i>OtherArg4</i> parameters.</p>

<p>To obtain these parameter values, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549969">WdfRequestGetParameters</a> and use the <b>DeviceIoControl</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552472">WDF_REQUEST_PARAMETERS</a> structure that is returned. </p>

<p>For more information about forwarding an I/O request, see <a href="wdf.forwarding_i_o_requests">Forwarding I/O Requests</a>.</p>

<p>Drivers often divide received I/O requests into smaller requests that they send to an I/O target, so your driver might create new requests.</p>

<p>To create a new I/O request:</p>

<p>Supply a <b>NULL</b> request handle for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>Request</i> parameter, or create a new request object and supply its handle:<ul>
<li>If you supply a <b>NULL</b> request handle, the framework uses an internal request object. This technique is simple to use, but the driver cannot cancel the request.</li>
<li>If you call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> to create one or more request objects, you can reuse these request objects by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>. This technique enables your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function to preallocate request objects for a device. Additionally, another driver thread can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549941">WdfRequestCancelSentRequest</a> to cancel the request, if necessary.</li>
</ul>
</p>

<p>Your driver can specify a non-<b>NULL</b> <i>RequestOptions</i> parameter, whether the driver provides a non-<b>NULL</b> or a <b>NULL</b> <i>Request</i> parameter. You can, for example, use the <i>RequestOptions</i> parameter to specify a time-out value. </p>

<p>Provide context space for the <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> method's <i>OtherArg1</i>,<i>OtherArg2</i>, and <i>OtherArg4</i> parameters, if the request requires them.</p>

<p>Your driver can specify this context space as locally allocated buffers, as WDFMEMORY handles, or as memory descriptor lists (MDLs). You can use whichever method is most convenient. </p>

<p>The following techniques to specify buffer space are available:</p>

<p>Supply local buffers.</p>

<p>Because <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b> handles I/O requests synchronously, the driver can create request buffers that are local to the calling routine, as the following code example shows.</p>

<p>Supply WDFMEMORY handles.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548706">WdfMemoryCreate</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548712">WdfMemoryCreatePreallocated</a> to obtain a handle to framework-managed memory, as the following code example shows. </p>

<p>Supply MDLs.</p>

<p>Drivers can obtain MDLs that are associated with a received I/O request by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550016">WdfRequestRetrieveInputWdmMdl</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff550021">WdfRequestRetrieveOutputWdmMdl</a>.</p>

<p>For information about obtaining status information after an I/O request completes, see <a href="wdf.completing_i_o_requests#obtaining_completion_information#obtaining_completion_information">Obtaining Completion Information</a>.</p>

<p>For more information about <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b>, see <a href="wdf.sending_i_o_requests_to_general_i_o_targets">Sending I/O Requests to General I/O Targets</a>.</p>

<p>For more information about I/O targets, see <a href="wdf.using_i_o_targets">Using I/O Targets</a>.</p>

<p>The following code example initializes an IEEE 1394 IRB structure, uses the structure's address to initialize a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552392">WDF_MEMORY_DESCRIPTOR</a> structure, and then calls <b>WdfIoTargetSendInternalIoctlOthersSynchronously</b>. </p>

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
<dt>Wdfiotarget.h (include Wdf.h)</dt>
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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544670">DeferredRequestCompleted</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547288">IoctlReqs</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551525">ReadReqs</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551603">RequestCompleted</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551609">RequestCompletedLocal</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff556209">WriteReqs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552392">WDF_MEMORY_DESCRIPTOR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552393">WDF_MEMORY_DESCRIPTOR_INIT_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552472">WDF_REQUEST_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546017">WdfDeviceGetIoTarget</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548591">WdfIoTargetCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548599">WdfIoTargetFormatRequestForInternalIoctlOthers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548706">WdfMemoryCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548712">WdfMemoryCreatePreallocated</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549941">WdfRequestCancelSentRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549969">WdfRequestGetParameters</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550016">WdfRequestRetrieveInputWdmMdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550021">WdfRequestRetrieveOutputWdmMdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfIoTargetSendInternalIoctlOthersSynchronously method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.wdfdevice.WdfDeviceEnqueueRequest
title: WdfDeviceEnqueueRequest
author: windows-driver-content
description: The WdfDeviceEnqueueRequest method delivers a specified I/O request to the framework, so that the framework can subsequently add the request to one of the I/O queues that the driver has created for the specified device.
old-location: wdf\wdfdeviceenqueuerequest.htm
ms.assetid: f669790f-0370-46a0-ba38-05e35cdf23b3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdevice.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfDeviceEnqueueRequest
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DeferredRequestCompleted, DriverCreate, KmdfIrql, KmdfIrql2, RequestCompleted, RequestCompletedLocal
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <= DISPATCH_LEVEL (See remarks section)
ms.keywords: WdfDeviceEnqueueRequest
req.iface: 
req.product: Windows 10 or later.
---

# WdfDeviceEnqueueRequest function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDeviceEnqueueRequest</b> method delivers a specified I/O request to the framework, so that the framework can subsequently add the request to one of the I/O queues that the driver has created for the specified device.</p>


## -syntax

````
NTSTATUS WdfDeviceEnqueueRequest(
  _In_ WDFDEVICE  Device,
  _In_ WDFREQUEST Request
);
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>Request</i> [in]

<dd>
<p>A handle to a framework request object.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the method returns STATUS_SUCCESS. Additional return values include:</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>The amount of available memory is low.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The driver has not created any I/O queues for the device, and the driver is not a filter driver.
</p><dl>
<dt><b>STATUS_WDF_BUSY</b></dt>
</dl><p>The device's I/O queue is not accepting requests.</p>

<p> </p>

<p>The method might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.</p>

## -remarks
<p>Your driver can call <b>WdfDeviceEnqueueRequest</b> only from an <a href="https://msdn.microsoft.com/b8bcea29-e404-490e-9d0c-02c96a5690ab">EvtIoInCallerContext</a> callback function.</p>

<p>The <b>WdfDeviceEnqueueRequest</b> method adds the request to the driver's request-type-specific I/O queue for the device, if the driver has created one. Otherwise the method adds the request to the device's default queue, if the driver has created one.</p>

<p>If the driver has not created any I/O queues for the device, <b>WdfDeviceEnqueueRequest</b> does the following:</p>

<p>If the driver is a filter driver, <b>WdfDeviceEnqueueRequest</b> sends the request to the driver's I/O target.</p>

<p>If the driver is not a filter driver, <b>WdfDeviceEnqueueRequest</b> returns STATUS_INVALID_DEVICE_REQUEST.</p>

<p>While <b>WdfDeviceEnqueueRequest</b> is executing, it is possible for the driver to receive and complete or cancel the request.</p>

<p>As a result, if the driver needs to use the request or its context after calling <b>WdfDeviceEnqueueRequest</b>, then it should take a reference on the request before calling <b>WdfDeviceEnqueueRequest</b>.</p>

<p>To do so, the driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548758">WdfObjectReference</a> before and then <a href="https://msdn.microsoft.com/library/windows/hardware/ff548739">WdfObjectDereference</a> after the call to <b>WdfDeviceEnqueueRequest</b>. The driver must dereference the request before exiting <a href="https://msdn.microsoft.com/b8bcea29-e404-490e-9d0c-02c96a5690ab">EvtIoInCallerContext</a>.</p>

<p>For more information about the <b>WdfDeviceEnqueueRequest</b> method, see <a href="wdf.managing_i_o_queues">Managing I/O Queues</a>.</p>

<p>For versions 1.0 and 1.5 of KMDF, <b>WdfDeviceEnqueueRequest</b> must be called at PASSIVE_LEVEL. For versions 1.7 and later, <b>WdfDeviceEnqueueRequest</b> can be called at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>The following code example is an <a href="https://msdn.microsoft.com/b8bcea29-e404-490e-9d0c-02c96a5690ab">EvtIoInCallerContext</a> callback function that looks for requests that contain the custom I/O control code, IOCTL_NONPNP_METHOD_NEITHER. If the I/O control code is not found, the callback function just returns the request to the framework. If the callback function finds the I/O control code, it preprocesses the request and then returns it to the framework. If an error is encountered, the callback function completes the request.</p>

<p>Your driver can call <b>WdfDeviceEnqueueRequest</b> only from an <a href="https://msdn.microsoft.com/b8bcea29-e404-490e-9d0c-02c96a5690ab">EvtIoInCallerContext</a> callback function.</p>

<p>The <b>WdfDeviceEnqueueRequest</b> method adds the request to the driver's request-type-specific I/O queue for the device, if the driver has created one. Otherwise the method adds the request to the device's default queue, if the driver has created one.</p>

<p>If the driver has not created any I/O queues for the device, <b>WdfDeviceEnqueueRequest</b> does the following:</p>

<p>If the driver is a filter driver, <b>WdfDeviceEnqueueRequest</b> sends the request to the driver's I/O target.</p>

<p>If the driver is not a filter driver, <b>WdfDeviceEnqueueRequest</b> returns STATUS_INVALID_DEVICE_REQUEST.</p>

<p>While <b>WdfDeviceEnqueueRequest</b> is executing, it is possible for the driver to receive and complete or cancel the request.</p>

<p>As a result, if the driver needs to use the request or its context after calling <b>WdfDeviceEnqueueRequest</b>, then it should take a reference on the request before calling <b>WdfDeviceEnqueueRequest</b>.</p>

<p>To do so, the driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548758">WdfObjectReference</a> before and then <a href="https://msdn.microsoft.com/library/windows/hardware/ff548739">WdfObjectDereference</a> after the call to <b>WdfDeviceEnqueueRequest</b>. The driver must dereference the request before exiting <a href="https://msdn.microsoft.com/b8bcea29-e404-490e-9d0c-02c96a5690ab">EvtIoInCallerContext</a>.</p>

<p>For more information about the <b>WdfDeviceEnqueueRequest</b> method, see <a href="wdf.managing_i_o_queues">Managing I/O Queues</a>.</p>

<p>For versions 1.0 and 1.5 of KMDF, <b>WdfDeviceEnqueueRequest</b> must be called at PASSIVE_LEVEL. For versions 1.7 and later, <b>WdfDeviceEnqueueRequest</b> can be called at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>The following code example is an <a href="https://msdn.microsoft.com/b8bcea29-e404-490e-9d0c-02c96a5690ab">EvtIoInCallerContext</a> callback function that looks for requests that contain the custom I/O control code, IOCTL_NONPNP_METHOD_NEITHER. If the I/O control code is not found, the callback function just returns the request to the framework. If the callback function finds the I/O control code, it preprocesses the request and then returns it to the framework. If an error is encountered, the callback function completes the request.</p>

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
<dt>Wdfdevice.h (include Wdf.h)</dt>
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
<p>&lt;= DISPATCH_LEVEL (See remarks section)</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544670">DeferredRequestCompleted</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551603">RequestCompleted</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551609">RequestCompletedLocal</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552476">WDF_REQUEST_PARAMETERS_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549945">WdfRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549969">WdfRequestGetParameters</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDeviceEnqueueRequest method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
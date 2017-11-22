---
UID: NC.udecxusbendpoint.EVT_UDECX_USB_ENDPOINT_RESET
title: EVT_UDECX_USB_ENDPOINT_RESET
author: windows-driver-content
description: The USB device emulation class extension (UdeCx) invokes this callback function to reset an endpoint of the virtual USB device.
old-location: buses\evt_udecx_usb_endpoint_reset.htm
ms.assetid: 4220509B-A378-47F4-8E71-0290EDED89EB
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: usbref
req.header: udecxusbendpoint.h
req.include-header: Udecx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 
req.alt-api: EvtUsbEndpointReset
req.alt-loc: UdecxUsbEndpoint.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: UDECX_USB_ENDPOINT_INIT_AND_METADATA, UDECX_USB_ENDPOINT_INIT_AND_METADATA, *PUDECX_USB_ENDPOINT_INIT_AND_METADATA
req.iface: 
req.product: Windows 10 or later.
---

# EVT_UDECX_USB_ENDPOINT_RESET callback



## -description
<p>The USB device emulation class extension (UdeCx) invokes this callback function to reset an endpoint of the virtual USB device.</p>


## -prototype

````
EVT_UDECX_USB_ENDPOINT_RESET EvtUsbEndpointReset;

void EvtUsbEndpointReset(
  _In_ UDECXUSBENDPOINT UdecxUsbEndpoint,
  _In_ WDFREQUEST       Request
)
{ ... }
````


## -parameters
<dl>

### -param <i>UdecxUsbEndpoint</i> [in]

<dd>
<p>A handle to a UDE endpoint object that represents the endpoint to reset. The client driver retrieved this pointer in the previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/mt627983">UdecxUsbEndpointCreate</a>.</p>
</dd>

### -param <i>Request</i> [in]

<dd>
<p>A handle to a framework request object that represents the request to reset the endpoint.</p>
</dd>
</dl>

## -returns
<p>This callback function does not return a value.</p>

## -remarks
<p>The client driver registered this callback function in a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/mt627985">UdecxUsbEndpointInitSetCallbacks</a> by supplying a function pointer to its implementation.</p>

<p>The reset request clears the error condition in the endpoint that causes failed I/O transfers. At that time, UdeCx can invoke the  <i>EVT_UDECX_USB_ENDPOINT_RESET</i> callback function. That call is asynchronous. The client driver completes the request and signals completion with status by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a> method .  (this is the only way the UDECX client uses the request parameter).
</p>

<p>The client driver registered this callback function in a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/mt627985">UdecxUsbEndpointInitSetCallbacks</a> by supplying a function pointer to its implementation.</p>

<p>The reset request clears the error condition in the endpoint that causes failed I/O transfers. At that time, UdeCx can invoke the  <i>EVT_UDECX_USB_ENDPOINT_RESET</i> callback function. That call is asynchronous. The client driver completes the request and signals completion with status by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549948">WdfRequestCompleteWithInformation</a> method .  (this is the only way the UDECX client uses the request parameter).
</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.15</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>UdecxUsbEndpoint.h (include Udecx.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh968307">How to recover from USB pipe errors</a>
</dt>
<dt>
<a href="wdf.managing_i_o_queues">Managing I/O Queues</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt595932">Architecture: USB Device Emulation (UDE)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt595939">Write a UDE client driver</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20EVT_UDECX_USB_ENDPOINT_RESET callback function%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
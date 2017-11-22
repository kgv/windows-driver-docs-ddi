---
UID: NI.ufxbase.IOCTL_INTERNAL_USBFN_DESCRIPTOR_UPDATE
title: IOCTL_INTERNAL_USBFN_DESCRIPTOR_UPDATE
author: windows-driver-content
description: The USB function class extension sends this request to the client driver to update to the endpoint descriptor for the specified endpoint.
old-location: buses\ioctl_internal_usbfn_descriptor_update.htm
ms.assetid: 9BA9BC9E-C04C-48F8-B76A-2D6F779BBE05
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: usbref
req.header: ufxbase.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_INTERNAL_USBFN_DESCRIPTOR_UPDATE
req.alt-loc: ufxbase.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: PUFS_UNIT_DESCRIPTOR, UFS_UNIT_DESCRIPTOR, *PUFS_UNIT_DESCRIPTOR
req.iface: 
req.product: Windows 10 or later.
---

# IOCTL_INTERNAL_USBFN_DESCRIPTOR_UPDATE IOCTL



## -description
<p>The USB function class extension sends this request to the client driver to update to the endpoint descriptor for the specified endpoint.</p>


## -ioctlparameters

### -input-buffer
<p>The input buffer points to a <b>USBFNPIPEID</b> that specifies the pipe ID for the endpoint.</p>

### -input-buffer-length
<p>The size of a <b>USBFNPIPEID</b> value.</p>

<p>The size of a <b>USBFNPIPEID</b> value.</p>

### -output-buffer
<p>The output buffer points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure that describes the endpoint descriptor. To retrieve the structure, the client driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550018">WdfRequestRetrieveOutputBuffer</a>.</p>

<p>The output buffer points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure that describes the endpoint descriptor. To retrieve the structure, the client driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550018">WdfRequestRetrieveOutputBuffer</a>.</p>

<p>The output buffer points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure that describes the endpoint descriptor. To retrieve the structure, the client driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff550018">WdfRequestRetrieveOutputBuffer</a>.</p>

### -output-buffer-length
<p>The size of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure.</p>

<p>The size of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure.</p>

<p>The size of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure.</p>

<p>The size of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539317">USB_ENDPOINT_DESCRIPTOR</a> structure.</p>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p>
		  The client driver shall complete the request with <b>STATUS_SUCCESS</b> if the request is successful. 
		  Otherwise, the client driver shall complete the driver with to the appropriate error condition, 
		  such as <b>STATUS_INVALID_PARAMETER</b> or <b>STATUS_INSUFFICIENT_RESOURCES</b>.</p>

<p>
		  The client driver shall complete the request with <b>STATUS_SUCCESS</b> if the request is successful. 
		  Otherwise, the client driver shall complete the driver with to the appropriate error condition, 
		  such as <b>STATUS_INVALID_PARAMETER</b> or <b>STATUS_INSUFFICIENT_RESOURCES</b>.</p>

<p>
		  The client driver shall complete the request with <b>STATUS_SUCCESS</b> if the request is successful. 
		  Otherwise, the client driver shall complete the driver with to the appropriate error condition, 
		  such as <b>STATUS_INVALID_PARAMETER</b> or <b>STATUS_INSUFFICIENT_RESOURCES</b>.</p>

<p>
		  The client driver shall complete the request with <b>STATUS_SUCCESS</b> if the request is successful. 
		  Otherwise, the client driver shall complete the driver with to the appropriate error condition, 
		  such as <b>STATUS_INVALID_PARAMETER</b> or <b>STATUS_INSUFFICIENT_RESOURCES</b>.</p>

<p>
		  The client driver shall complete the request with <b>STATUS_SUCCESS</b> if the request is successful. 
		  Otherwise, the client driver shall complete the driver with to the appropriate error condition, 
		  such as <b>STATUS_INVALID_PARAMETER</b> or <b>STATUS_INSUFFICIENT_RESOURCES</b>.</p>

## -remarks
<p>UFX sends this IOCTL to the command queue created for the endpoint by <a href="https://msdn.microsoft.com/library/windows/hardware/mt187965">UfxEndpointCreate</a>.  The client driver is expected to update the configuration of the endpoint on the controller with the parameters contained in the endpoint descriptor.</p>

<p>UFX sends this IOCTL to the command queue created for the endpoint by <a href="https://msdn.microsoft.com/library/windows/hardware/mt187965">UfxEndpointCreate</a>.  The client driver is expected to update the configuration of the endpoint on the controller with the parameters contained in the endpoint descriptor.</p>

<p>UFX sends this IOCTL to the command queue created for the endpoint by <a href="https://msdn.microsoft.com/library/windows/hardware/mt187965">UfxEndpointCreate</a>.  The client driver is expected to update the configuration of the endpoint on the controller with the parameters contained in the endpoint descriptor.</p>

<p>UFX sends this IOCTL to the command queue created for the endpoint by <a href="https://msdn.microsoft.com/library/windows/hardware/mt187965">UfxEndpointCreate</a>.  The client driver is expected to update the configuration of the endpoint on the controller with the parameters contained in the endpoint descriptor.</p>

<p>UFX sends this IOCTL to the command queue created for the endpoint by <a href="https://msdn.microsoft.com/library/windows/hardware/mt187965">UfxEndpointCreate</a>.  The client driver is expected to update the configuration of the endpoint on the controller with the parameters contained in the endpoint descriptor.</p>

<p>UFX sends this IOCTL to the command queue created for the endpoint by <a href="https://msdn.microsoft.com/library/windows/hardware/mt187965">UfxEndpointCreate</a>.  The client driver is expected to update the configuration of the endpoint on the controller with the parameters contained in the endpoint descriptor.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ufxbase.h</dt>
</dl>
</td>
</tr>
</table>
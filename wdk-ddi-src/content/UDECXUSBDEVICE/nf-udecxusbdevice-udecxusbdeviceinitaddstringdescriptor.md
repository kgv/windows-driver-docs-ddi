---
UID: NF.udecxusbdevice.UdecxUsbDeviceInitAddStringDescriptor
title: UdecxUsbDeviceInitAddStringDescriptor
author: windows-driver-content
description: Adds a USB string descriptor to the initialization parameters used to create a virtual USB device.
old-location: buses\udecxusbdeviceinitaddstringdescriptor.htm
ms.assetid: 05971A19-4B66-41F6-9043-DA9C81FA92E5
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: usbref
req.header: udecxusbdevice.h
req.include-header: Udecx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 
req.alt-api: UdecxUsbDeviceInitAddStringDescriptor
req.alt-loc: Udecxstub.lib,Udecxstub.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Udecxstub.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: UdecxUsbDeviceInitAddStringDescriptor
req.iface: 
req.product: Windows 10 or later.
---

# UdecxUsbDeviceInitAddStringDescriptor function



## -description
<p>Adds a USB string descriptor to the initialization parameters used to create a virtual USB device. </p>


## -syntax

````
NTSTATUS UdecxUsbDeviceInitAddStringDescriptor(
  _Inout_ PUDECXUSBDEVICE_INIT UdecxUsbDeviceInit,
  _In_    PCUNICODE_STRING     String,
  _In_    UCHAR                DescriptorIndex,
  _In_    USHORT               LanguageId
);
````


## -parameters
<dl>

### -param <i>UdecxUsbDeviceInit</i> [in, out]

<dd>
<p>A pointer to a WDF-allocated structure that contains initialization parameters for the virtual USB device.  The client driver retrieved this pointer in the previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/mt627968">UdecxUsbDeviceInitAllocate</a>. </p>
</dd>

### -param <i>String</i> [in]

<dd>
<p>A Unicode string that contains the USB string descriptor to add to the device.</p>
</dd>

### -param <i>DescriptorIndex</i> [in]

<dd>
<p>The index of the descriptor.</p>
</dd>

### -param <i>LanguageId</i> [in]

<dd>
<p>The language identifier of the string. The client driver must define constants for the language support, such as:</p>
<p><code>const USHORT US_ENGLISH = 0x409;
</code></p>
</dd>
</dl>

## -returns
<p>The method returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method might return an appropriate <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> error code. </p>

## -remarks


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
<dt>UdecxUsbDevice.h (include Udecx.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Udecxstub.lib</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt627968">UdecxUsbDeviceInitAllocate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540156">USB String Descriptors</a>
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
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20UdecxUsbDeviceInitAddStringDescriptor function%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
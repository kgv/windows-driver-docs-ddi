---
UID: NS.usbioctl._USB_HUB_INFORMATION
title: USB_HUB_INFORMATION
author: windows-driver-content
description: The USB_HUB_INFORMATION structure contains information about a hub.
old-location: buses\usb_hub_information.htm
ms.assetid: f65789b6-b2d1-4e5d-92b3-10730e76661a
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: usbref
req.header: usbioctl.h
req.include-header: Usbioctl.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: USB_HUB_INFORMATION
req.alt-loc: usbioctl.h
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
ms.keywords: USB_HUB_INFORMATION, USB_HUB_INFORMATION, *PUSB_HUB_INFORMATION
req.iface: 
req.product: Windows 10 or later.
---

# USB_HUB_INFORMATION structure



## -description
<p>The <b>USB_HUB_INFORMATION</b> structure contains information about a hub.</p>


## -syntax

````
typedef struct _USB_HUB_INFORMATION {
  USB_HUB_DESCRIPTOR HubDescriptor;
  BOOLEAN            HubIsBusPowered;
} USB_HUB_INFORMATION, *PUSB_HUB_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>HubDescriptor</b>

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff539331">USB_HUB_DESCRIPTOR</a> structure that contains selected information from the hub descriptor.</p>
</dd>

### -field <b>HubIsBusPowered</b>

<dd>
<p>A Boolean value that indicates whether the hub is bus-powered. <b>TRUE</b>, the hub is bus-powered; <b>FALSE</b>, the hub is self-powered.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Usbioctl.h (include Usbioctl.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539331">USB_HUB_DESCRIPTOR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540110">USB_NODE_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540160">USB Structures</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20USB_HUB_INFORMATION structure%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
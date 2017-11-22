---
UID: NF.wdfusb.WDF_USB_DEVICE_CREATE_CONFIG_INIT
title: WDF_USB_DEVICE_CREATE_CONFIG_INIT
author: windows-driver-content
description: The WDF_USB_DEVICE_CREATE_CONFIG_INIT function initializes a WDF_USB_DEVICE_CREATE_CONFIG structure.
old-location: wdf\wdf_usb_device_create_config_init.htm
ms.assetid: 01053A65-45A4-4232-A9F2-1651DC820026
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfusb.h
req.include-header: Wdfusb.h
req.target-type: Universal
req.target-min-winverclnt: Windows Vista
req.target-min-winversvr: 
req.kmdf-ver: 1.11
req.umdf-ver: 2.0
req.alt-api: WDF_USB_DEVICE_CREATE_CONFIG_INIT
req.alt-loc: wdfusb.h
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
ms.keywords: WDF_USB_DEVICE_CREATE_CONFIG_INIT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_USB_DEVICE_CREATE_CONFIG_INIT function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WDF_USB_DEVICE_CREATE_CONFIG_INIT</b> function
  initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/hh406503">WDF_USB_DEVICE_CREATE_CONFIG</a> structure. </p>


## -syntax

````
void WDF_USB_DEVICE_CREATE_CONFIG_INIT(
  _Out_ PWDF_USB_DEVICE_CREATE_CONFIG Config,
  _In_  ULONG                         USBDClientContractVersion
);
````


## -parameters
<dl>

### -param <i>Config</i> [out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh406503">WDF_USB_DEVICE_CREATE_CONFIG</a> structure.</p>
</dd>

### -param <i>USBDClientContractVersion</i> [in]

<dd>
<p>The contract version that the client driver supports. <b>USBDClientContractVersion</b> must be USBD_CLIENT_CONTRACT_VERSION_602. </p>
</dd>
</dl>

## -returns
<p>This function does not return a value.</p>

## -remarks
<p>The <b>WDF_USB_DEVICE_CREATE_CONFIG_INIT</b> function zeros the specified <a href="https://msdn.microsoft.com/library/windows/hardware/hh406503">WDF_USB_DEVICE_CREATE_CONFIG</a> structure and sets the <b>Size</b> member to the size of the structure. It also sets the structure's <b>USBDClientContractVersion</b> member to the specified value.</p>

<p>For a code example that uses <b>WDF_USB_DEVICE_CREATE_CONFIG_INIT</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/hh439428">WdfUsbTargetDeviceCreateWithParameters</a>.</p>

<p>The <b>WDF_USB_DEVICE_CREATE_CONFIG_INIT</b> function zeros the specified <a href="https://msdn.microsoft.com/library/windows/hardware/hh406503">WDF_USB_DEVICE_CREATE_CONFIG</a> structure and sets the <b>Size</b> member to the size of the structure. It also sets the structure's <b>USBDClientContractVersion</b> member to the specified value.</p>

<p>For a code example that uses <b>WDF_USB_DEVICE_CREATE_CONFIG_INIT</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/hh439428">WdfUsbTargetDeviceCreateWithParameters</a>.</p>

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
<p>Minimum support</p>
</th>
<td width="70%">
<p>Windows Vista</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.11</p>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406503">WDF_USB_DEVICE_CREATE_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439428">WdfUsbTargetDeviceCreateWithParameters</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_USB_DEVICE_CREATE_CONFIG_INIT function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
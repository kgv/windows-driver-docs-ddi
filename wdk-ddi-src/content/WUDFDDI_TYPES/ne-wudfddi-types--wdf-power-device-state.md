---
UID: NE.wudfddi_types._WDF_POWER_DEVICE_STATE
title: WDF_POWER_DEVICE_STATE
author: windows-driver-content
description: The WDF_POWER_DEVICE_STATE enumeration contains values that identify the power state that a device might support.
old-location: wdf\wdf_power_device_state_umdf.htm
ms.assetid: de92bf06-b8fa-4c16-9216-95d68ca75111
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi_types.h
req.include-header: Wudfddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WDF_POWER_DEVICE_STATE
req.alt-loc: Wudfddi_types.h
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
ms.keywords: WRITE_REGISTER_USHORT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_POWER_DEVICE_STATE enumeration



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>
      The <a href="https://msdn.microsoft.com/library/windows/hardware/ff552421">WDF_POWER_DEVICE_STATE</a> enumeration contains values that identify the power state that a device might support.</p>


## -syntax

````
typedef enum _WDF_POWER_DEVICE_STATE { 
  WdfPowerDeviceInvalid                = 0,
  WdfPowerDeviceD0                     = 1,
  WdfPowerDeviceD1                     = 2,
  WdfPowerDeviceD2                     = 3,
  WdfPowerDeviceD3                     = 4,
  WdfPowerDeviceD3Final                = 5,
  WdfPowerDevicePrepareForHibernation  = 6,
  WdfPowerDeviceMaximum                = ( WdfPowerDevicePrepareForHibernation + 1 )
} WDF_POWER_DEVICE_STATE;
````


## -enum-fields
<dl>

### -field <a id="WdfPowerDeviceInvalid"></a><a id="wdfpowerdeviceinvalid"></a><a id="WDFPOWERDEVICEINVALID"></a><b>WdfPowerDeviceInvalid</b>

<dd>
<p>The device power state is invalid or unknown.</p>
</dd>

### -field <a id="WdfPowerDeviceD0"></a><a id="wdfpowerdeviced0"></a><a id="WDFPOWERDEVICED0"></a><b>WdfPowerDeviceD0</b>

<dd>
<p>The device supports the D0 device power state.</p>
</dd>

### -field <a id="WdfPowerDeviceD1"></a><a id="wdfpowerdeviced1"></a><a id="WDFPOWERDEVICED1"></a><b>WdfPowerDeviceD1</b>

<dd>
<p>The device supports the D1 device power state.</p>
</dd>

### -field <a id="WdfPowerDeviceD2"></a><a id="wdfpowerdeviced2"></a><a id="WDFPOWERDEVICED2"></a><b>WdfPowerDeviceD2</b>

<dd>
<p>The device supports the D2 device power state.</p>
</dd>

### -field <a id="WdfPowerDeviceD3"></a><a id="wdfpowerdeviced3"></a><a id="WDFPOWERDEVICED3"></a><b>WdfPowerDeviceD3</b>

<dd>
<p>The device supports the D3 device power state.</p>
</dd>

### -field <a id="WdfPowerDeviceD3Final"></a><a id="wdfpowerdeviced3final"></a><a id="WDFPOWERDEVICED3FINAL"></a><b>WdfPowerDeviceD3Final</b>

<dd>
<p>The final time that the device enters the D3 device power state. Typically, this value means that the computer's power is being turned off or the device is being removed from the computer. The device might have been already removed.</p>
</dd>

### -field <a id="WdfPowerDevicePrepareForHibernation"></a><a id="wdfpowerdeviceprepareforhibernation"></a><a id="WDFPOWERDEVICEPREPAREFORHIBERNATION"></a><b>WdfPowerDevicePrepareForHibernation</b>

<dd>
<p>The device supports hibernation files, and the computer is ready to hibernate by entering system state S4. The driver must not turn off the device.</p>
</dd>

### -field <a id="WdfPowerDeviceMaximum"></a><a id="wdfpowerdevicemaximum"></a><a id="WDFPOWERDEVICEMAXIMUM"></a><b>WdfPowerDeviceMaximum</b>

<dd>
<p>Valid enumeration values were exceeded.</p>
</dd>
</dl>

## -remarks
<p>The framework supplies one of the values of <a href="https://msdn.microsoft.com/library/windows/hardware/ff552421">WDF_POWER_DEVICE_STATE</a> to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556799">IPnpCallback::OnD0Entry</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff556803">IPnpCallback::OnD0Exit</a> method to notify the UMDF driver about the power state of the device.</p>

<p>The framework supplies one of the values of <a href="https://msdn.microsoft.com/library/windows/hardware/ff552421">WDF_POWER_DEVICE_STATE</a> to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556799">IPnpCallback::OnD0Entry</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff556803">IPnpCallback::OnD0Exit</a> method to notify the UMDF driver about the power state of the device.</p>

<p>The framework supplies one of the values of <a href="https://msdn.microsoft.com/library/windows/hardware/ff552421">WDF_POWER_DEVICE_STATE</a> to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556799">IPnpCallback::OnD0Entry</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff556803">IPnpCallback::OnD0Exit</a> method to notify the UMDF driver about the power state of the device.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi_types.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556799">IPnpCallback::OnD0Entry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556803">IPnpCallback::OnD0Exit</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_POWER_DEVICE_STATE enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
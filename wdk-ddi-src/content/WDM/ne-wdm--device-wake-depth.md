---
UID: NE.wdm._DEVICE_WAKE_DEPTH
title: DEVICE_WAKE_DEPTH
author: windows-driver-content
description: The DEVICE_WAKE_DEPTH enumeration specifies the deepest device power state from which a device can trigger a wake signal.
old-location: kernel\device_wake_depth.htm
ms.assetid: C8829785-1EB7-4F29-9279-F2FC2A3C0ABD
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DEVICE_WAKE_DEPTH
req.alt-loc: Wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: WDI_TYPE_PMK_NAME, WDI_TYPE_PMK_NAME, *PWDI_TYPE_PMK_NAME
req.iface: 
req.product: Windows 10 or later.
---

# DEVICE_WAKE_DEPTH enumeration



## -description
<p>The <b>DEVICE_WAKE_DEPTH</b> enumeration specifies the deepest device power state from which a device can trigger a wake signal.</p>


## -syntax

````
typedef enum _DEVICE_WAKE_DEPTH { 
  DeviceWakeDepthNotWakeable  = 0,
  DeviceWakeDepthD0,
  DeviceWakeDepthD1,
  DeviceWakeDepthD2,
  DeviceWakeDepthD3hot,
  DeviceWakeDepthD3cold,
  DeviceWakeDepthMaximum
} DEVICE_WAKE_DEPTH;
````


## -enum-fields
<dl>

### -field <a id="DeviceWakeDepthNotWakeable"></a><a id="devicewakedepthnotwakeable"></a><a id="DEVICEWAKEDEPTHNOTWAKEABLE"></a><b>DeviceWakeDepthNotWakeable</b>

<dd>
<p>There is no device power state that can trigger a wake signal.</p>
</dd>

### -field <a id="DeviceWakeDepthD0"></a><a id="devicewakedepthd0"></a><a id="DEVICEWAKEDEPTHD0"></a><b>DeviceWakeDepthD0</b>

<dd>
<p>D0 is the deepest device power state from which the device can trigger a wake signal. For more information, see Remarks.</p>
</dd>

### -field <a id="DeviceWakeDepthD1"></a><a id="devicewakedepthd1"></a><a id="DEVICEWAKEDEPTHD1"></a><b>DeviceWakeDepthD1</b>

<dd>
<p>D1 is the deepest low-power device power state from which the device can trigger a wake signal.</p>
</dd>

### -field <a id="DeviceWakeDepthD2"></a><a id="devicewakedepthd2"></a><a id="DEVICEWAKEDEPTHD2"></a><b>DeviceWakeDepthD2</b>

<dd>
<p>D2 is the deepest low-power device power state from which the device can trigger a wake signal.</p>
</dd>

### -field <a id="DeviceWakeDepthD3hot"></a><a id="devicewakedepthd3hot"></a><a id="DEVICEWAKEDEPTHD3HOT"></a><b>DeviceWakeDepthD3hot</b>

<dd>
<p>D3hot is the deepest low-power device power state from which the device can trigger a wake signal.</p>
</dd>

### -field <a id="DeviceWakeDepthD3cold"></a><a id="devicewakedepthd3cold"></a><a id="DEVICEWAKEDEPTHD3COLD"></a><b>DeviceWakeDepthD3cold</b>

<dd>
<p>D3cold is the deepest low-power device power state from which the device can trigger a wake signal.</p>
</dd>

### -field <a id="DeviceWakeDepthMaximum"></a><a id="devicewakedepthmaximum"></a><a id="DEVICEWAKEDEPTHMAXIMUM"></a><b>DeviceWakeDepthMaximum</b>

<dd>
<p>Reserved for use by the operating system.</p>
</dd>
</dl>

## -remarks
<p>The <i>DeepestWakeableDstate</i> parameter of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh967712">GetIdleWakeInfo</a> routine is a pointer to a variable of type <b>DEVICE_WAKE_DEPTH</b>.</p>

<p>The drivers for most devices have no reason to arm a wake signal when the device is in D0. These drivers can treat the <b>DeviceWakeDepthD0</b> output value as equivalent to a call to the <i>GetIdleWakeInfo</i> routine that fails and returns an error status.</p>

<p>The <i>DeepestWakeableDstate</i> parameter of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh967712">GetIdleWakeInfo</a> routine is a pointer to a variable of type <b>DEVICE_WAKE_DEPTH</b>.</p>

<p>The drivers for most devices have no reason to arm a wake signal when the device is in D0. These drivers can treat the <b>DeviceWakeDepthD0</b> output value as equivalent to a call to the <i>GetIdleWakeInfo</i> routine that fails and returns an error status.</p>

<p>The <i>DeepestWakeableDstate</i> parameter of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh967712">GetIdleWakeInfo</a> routine is a pointer to a variable of type <b>DEVICE_WAKE_DEPTH</b>.</p>

<p>The drivers for most devices have no reason to arm a wake signal when the device is in D0. These drivers can treat the <b>DeviceWakeDepthD0</b> output value as equivalent to a call to the <i>GetIdleWakeInfo</i> routine that fails and returns an error status.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967712">GetIdleWakeInfo</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20DEVICE_WAKE_DEPTH enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
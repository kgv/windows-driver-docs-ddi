---
UID: NF.wdfdevice.WdfDeviceSetCharacteristics
title: WdfDeviceSetCharacteristics
author: windows-driver-content
description: The WdfDeviceSetCharacteristics method sets device characteristics for a specified device.
old-location: wdf\wdfdevicesetcharacteristics.htm
ms.assetid: 07b5d7ed-fc4c-45e5-8748-2630c91d912a
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
req.alt-api: WdfDeviceSetCharacteristics
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfDeviceSetCharacteristics
req.iface: 
req.product: Windows 10 or later.
---

# WdfDeviceSetCharacteristics function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDeviceSetCharacteristics</b> method sets device characteristics for a specified device.</p>


## -syntax

````
VOID WdfDeviceSetCharacteristics(
  _In_ WDFDEVICE Device,
  _In_ ULONG     DeviceCharacteristics
);
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>DeviceCharacteristics</i> [in]

<dd>
<p>A value that consists of ORed system-defined constants that represent device characteristics. For more information, see the <b>Characteristics</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure.</p>
</dd>
</dl>

## -returns
<p>None.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.</p>

## -remarks
<p>You should set device characteristics by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546074">WdfDeviceInitSetCharacteristics</a> method in your <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>. If your driver cannot determine a device's characteristics until after the <i>EvtDriverDeviceAdd</i> callback function returns, the driver typically should call <b>WdfDeviceSetCharacteristics</b> in its <a href="https://msdn.microsoft.com/a3d4a983-8a75-44be-bd72-8673d89f9f87">EvtDevicePrepareHardware</a> callback function.</p>

<p>Each call to <b>WdfDeviceSetCharacteristics</b> overwrites the settings of any previous call.</p>

<p>The following code example sets the FILE_REMOVABLE_MEDIA characteristic for a specified device.</p>

<p>You should set device characteristics by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546074">WdfDeviceInitSetCharacteristics</a> method in your <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>. If your driver cannot determine a device's characteristics until after the <i>EvtDriverDeviceAdd</i> callback function returns, the driver typically should call <b>WdfDeviceSetCharacteristics</b> in its <a href="https://msdn.microsoft.com/a3d4a983-8a75-44be-bd72-8673d89f9f87">EvtDevicePrepareHardware</a> callback function.</p>

<p>Each call to <b>WdfDeviceSetCharacteristics</b> overwrites the settings of any previous call.</p>

<p>The following code example sets the FILE_REMOVABLE_MEDIA characteristic for a specified device.</p>

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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546074">WdfDeviceInitSetCharacteristics</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545960">WdfDeviceGetCharacteristics</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDeviceSetCharacteristics method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
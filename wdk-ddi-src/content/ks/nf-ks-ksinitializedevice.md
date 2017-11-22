---
UID: NF.ks.KsInitializeDevice
title: KsInitializeDevice
author: windows-driver-content
description: The KsInitializeDevice function is called by AVStream to initialize the AVStream device class from within KsCreateDevice.
old-location: stream\ksinitializedevice.htm
ms.assetid: f33122d0-7661-454a-87f7-7b5795793376
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsInitializeDevice
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: KsInitializeDevice
req.iface: 
---

# KsInitializeDevice function



## -description
<p>The<b> KsInitializeDevice </b>function is called by AVStream to initialize the AVStream device class from within <a href="https://msdn.microsoft.com/library/windows/hardware/ff561647">KsCreateDevice</a>.</p>


## -syntax

````
NTSTATUS KsInitializeDevice(
  _In_           PDEVICE_OBJECT      FunctionalDeviceObject,
  _In_           PDEVICE_OBJECT      PhysicalDeviceObject,
  _In_           PDEVICE_OBJECT      NextDeviceObject,
  _In_opt_ const KSDEVICE_DESCRIPTOR *Descriptor
);
````


## -parameters
<dl>

### -param <i>FunctionalDeviceObject</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure representing the WDM functional device object for the device being initialized. </p>
<p>Normally, this is returned from an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548397">IoCreateDevice</a> call. Minidrivers calling this function directly are responsible for calling <b>IoCreateDevice</b> and attaching themselves to the device stack.</p>
</dd>

### -param <i>PhysicalDeviceObject</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure representing the WDM physical device object for the device being initialized.</p>
</dd>

### -param <i>NextDeviceObject</i> [in]

<dd>
<p>A pointer to the next <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure in the device stack as determined by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff548300">IoAttachDeviceToDeviceStack</a>.</p>
</dd>

### -param <i>Descriptor</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561691">KSDEVICE_DESCRIPTOR</a> structure that describes the characteristics of the device being initialized. If this parameter is <b>NULL</b>, the device is initialized with the default characteristics and has no associated filter factories.</p>
</dd>
</dl>

## -returns
<p><b>KsInitializeDevice</b> returns STATUS_SUCCESS if the device was successfully initialized. Otherwise, it returns an appropriate error code.</p>

## -remarks
<p>Most minidrivers do not call this function directly. Only call <b>KsInitializeDevice</b> if your minidriver does not use <a href="https://msdn.microsoft.com/library/windows/hardware/ff562683">KsInitializeDriver</a> for initialization, handles <b>AddDevice</b> independently, and does not use <a href="https://msdn.microsoft.com/library/windows/hardware/ff560927">KsAddDevice</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff561647">KsCreateDevice</a> in its <b>AddDevice</b> handler. </p>

<p>Most minidrivers do not call this function directly. Only call <b>KsInitializeDevice</b> if your minidriver does not use <a href="https://msdn.microsoft.com/library/windows/hardware/ff562683">KsInitializeDriver</a> for initialization, handles <b>AddDevice</b> independently, and does not use <a href="https://msdn.microsoft.com/library/windows/hardware/ff560927">KsAddDevice</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff561647">KsCreateDevice</a> in its <b>AddDevice</b> handler. </p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562683">KsInitializeDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560927">KsAddDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561647">KsCreateDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567144">KsTerminateDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561681">KSDEVICE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548397">IoCreateDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548300">IoAttachDeviceToDeviceStack</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544174">DRIVER_OBJECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsInitializeDevice function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
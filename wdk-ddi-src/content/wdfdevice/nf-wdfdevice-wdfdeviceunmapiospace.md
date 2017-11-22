---
UID: NF.wdfdevice.WdfDeviceUnmapIoSpace
title: WdfDeviceUnmapIoSpace
author: windows-driver-content
description: The WdfDeviceUnmapIoSpace function unmaps a specified range of physical addresses previously mapped by the WdfDeviceMapIoSpace function.
old-location: wdf\wdfdeviceunmapiospace.htm
ms.assetid: C8963667-D2FB-4360-A523-33429D6FBF1B
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdevice.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 2.0
req.alt-api: WdfDeviceUnmapIoSpace
req.alt-loc: WUDFx02000.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: WUDFx02000.lib
req.dll: WUDFx02000.dll
req.irql: PASSIVE_LEVEL
ms.keywords: WdfDeviceUnmapIoSpace
req.iface: 
req.product: Windows 10 or later.
---

# WdfDeviceUnmapIoSpace function



## -description
<p class="CCE_Message">[Applies to UMDF only]</p>
<p>The <b>WdfDeviceUnmapIoSpace</b> function unmaps a specified range of physical addresses previously mapped by the <a href="https://msdn.microsoft.com/library/windows/hardware/dn265605">WdfDeviceMapIoSpace</a> function.</p>


## -syntax

````
void WdfDeviceUnmapIoSpace(
  _In_ WDFDEVICE Device,
  _In_ PVOID     PseudoBaseAddress,
  _In_ SIZE_T    NumberOfBytes
);
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>PseudoBaseAddress</i> [in]

<dd>
<p>The address of a location that receives a pointer to the pseudo base address.

</p>
</dd>

### -param <i>NumberOfBytes</i> [in]

<dd>
<p>Specifies a value greater than zero, indicating the number of bytes to be mapped.</p>
</dd>
</dl>

## -returns
<p>This function does not return a value.</p>

## -remarks
<p>This function is the UMDF version 2 equivalent of <a href="https://msdn.microsoft.com/E95AC8E6-222A-4C88-8EBD-6BD7F22B9F18">IWDFDevice3::UnmapIoSpace</a>.</p>

<p>If a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/dn265605">WdfDeviceMapIoSpace</a> in <a href="https://msdn.microsoft.com/a3d4a983-8a75-44be-bd72-8673d89f9f87">EvtDevicePrepareHardware</a> callback, it must call <b>WdfDeviceUnmapIoSpace</b> in its <a href="https://msdn.microsoft.com/b4c17e57-688c-4c76-892c-5c8abbf83f20">EvtDeviceReleaseHardware</a> callback.</p>

<p></p>

<p>This function is the UMDF version 2 equivalent of <a href="https://msdn.microsoft.com/E95AC8E6-222A-4C88-8EBD-6BD7F22B9F18">IWDFDevice3::UnmapIoSpace</a>.</p>

<p>If a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/dn265605">WdfDeviceMapIoSpace</a> in <a href="https://msdn.microsoft.com/a3d4a983-8a75-44be-bd72-8673d89f9f87">EvtDevicePrepareHardware</a> callback, it must call <b>WdfDeviceUnmapIoSpace</b> in its <a href="https://msdn.microsoft.com/b4c17e57-688c-4c76-892c-5c8abbf83f20">EvtDeviceReleaseHardware</a> callback.</p>

<p></p>

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
<p>Windows 8.1</p>
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
<dt>WUDFx02000.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx02000.dll</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/dn265605">WdfDeviceMapIoSpace</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/E95AC8E6-222A-4C88-8EBD-6BD7F22B9F18">IWDFDevice3::UnmapIoSpace</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDeviceUnmapIoSpace function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
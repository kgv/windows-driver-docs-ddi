---
UID: NF.video.VideoPortReleaseDeviceLock
title: VideoPortReleaseDeviceLock
author: windows-driver-content
description: The VideoPortReleaseDeviceLock function releases the device lock acquired in a prior call to VideoPortAcquireDeviceLock.
old-location: display\videoportreleasedevicelock.htm
ms.assetid: 932953c3-828f-4dcd-918e-5b3b5d8def1c
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows 2000 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: VideoPortReleaseDeviceLock
req.alt-loc: Videoprt.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Videoprt.lib
req.dll: Videoprt.sys
req.irql: PASSIVE_LEVEL
ms.keywords: VideoPortReleaseDeviceLock
req.iface: 
req.product: Windows 10 or later.
---

# VideoPortReleaseDeviceLock function



## -description
<p>The <b>VideoPortReleaseDeviceLock</b> function releases the device lock acquired in a prior call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff570174">VideoPortAcquireDeviceLock</a>.</p>


## -syntax

````
VOID VideoPortReleaseDeviceLock(
  _In_ PVOID HwDeviceExtension
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>Pointer to the miniport driver's device extension.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Typically, the video port driver guarantees threaded synchronization into the miniport driver by using of a device lock. However, a miniport driver must perform its own synchronization when being accessed by a child device; that is, a miniport driver must perform synchronization in routines that it exposes through <a href="https://msdn.microsoft.com/f16a7fa3-3471-4ccb-b1b4-982d33f930d3">HwVidQueryInterface</a>. The miniport driver does this by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff570174">VideoPortAcquireDeviceLock</a> to acquire the device lock maintained by the video port driver.</p>

<p>The miniport driver should call <b>VideoPortReleaseDeviceLock</b> to release the device lock as quickly as possible. </p>

<p>Typically, the video port driver guarantees threaded synchronization into the miniport driver by using of a device lock. However, a miniport driver must perform its own synchronization when being accessed by a child device; that is, a miniport driver must perform synchronization in routines that it exposes through <a href="https://msdn.microsoft.com/f16a7fa3-3471-4ccb-b1b4-982d33f930d3">HwVidQueryInterface</a>. The miniport driver does this by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff570174">VideoPortAcquireDeviceLock</a> to acquire the device lock maintained by the video port driver.</p>

<p>The miniport driver should call <b>VideoPortReleaseDeviceLock</b> to release the device lock as quickly as possible. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 2000 and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Videoprt.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Videoprt.sys</dt>
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
<a href="https://msdn.microsoft.com/f16a7fa3-3471-4ccb-b1b4-982d33f930d3">HwVidQueryInterface</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570174">VideoPortAcquireDeviceLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20VideoPortReleaseDeviceLock function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
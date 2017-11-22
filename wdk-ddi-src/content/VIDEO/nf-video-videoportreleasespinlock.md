---
UID: NF.video.VideoPortReleaseSpinLock
title: VideoPortReleaseSpinLock
author: windows-driver-content
description: The VideoPortReleaseSpinLock function releases ownership of a given spin lock and restores the original IRQL at which the caller was running.
old-location: display\videoportreleasespinlock.htm
ms.assetid: 8ce2006e-e66c-4b2d-8d26-2eba8d8e2864
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows XP and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: VideoPortReleaseSpinLock
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
req.irql: DISPATCH_LEVEL (see Remarks section)
ms.keywords: VideoPortReleaseSpinLock
req.iface: 
req.product: Windows 10 or later.
---

# VideoPortReleaseSpinLock function



## -description
<p>The <b>VideoPortReleaseSpinLock</b> function releases ownership of a given spin lock and restores the original IRQL at which the caller was running.</p>


## -syntax

````
VOID VideoPortReleaseSpinLock(
  _In_    PVOID      HwDeviceExtension,
  _Inout_ PSPIN_LOCK SpinLock,
  _In_    UCHAR      NewIrql
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>Pointer to the miniport driver's device extension.</p>
</dd>

### -param <i>SpinLock</i> [in, out]

<dd>
<p>Pointer to a memory location that contains the spin lock to be released.</p>
</dd>

### -param <i>NewIrql</i> [in]

<dd>
<p>Specifies the IRQL to be restored.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>This call is the inverse of <a href="https://msdn.microsoft.com/library/windows/hardware/ff570175">VideoPortAcquireSpinLock</a>. The <i>NewIrql</i> value must be the same as the value pointed to by <i>OldIrql</i> when <b>VideoPortAcquireSpinLock </b>returned.</p>

<p>Callers of <b>VideoPortReleaseSpinLock</b> must be running at IRQL = DISPATCH_LEVEL. On return from this routine, IRQL is restored to the <i>NewIrql</i> value.</p>

<p>This call is the inverse of <a href="https://msdn.microsoft.com/library/windows/hardware/ff570175">VideoPortAcquireSpinLock</a>. The <i>NewIrql</i> value must be the same as the value pointed to by <i>OldIrql</i> when <b>VideoPortAcquireSpinLock </b>returned.</p>

<p>Callers of <b>VideoPortReleaseSpinLock</b> must be running at IRQL = DISPATCH_LEVEL. On return from this routine, IRQL is restored to the <i>NewIrql</i> value.</p>

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
<p>Available in Windows XP and later versions of the Windows operating systems.</p>
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
<p>DISPATCH_LEVEL (see Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570175">VideoPortAcquireSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20VideoPortReleaseSpinLock function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
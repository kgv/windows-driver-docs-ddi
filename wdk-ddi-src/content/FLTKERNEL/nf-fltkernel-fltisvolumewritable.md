---
UID: NF.fltkernel.FltIsVolumeWritable
title: FltIsVolumeWritable
author: windows-driver-content
description: The FltIsVolumeWritable routine determines whether the disk device that corresponds to a volume or minifilter driver instance is writable.
old-location: ifsk\fltisvolumewritable.htm
ms.assetid: 9347bc8d-e8fb-440c-8ceb-ce5e8cb1429e
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: The FltIsVolumeWritable routine is available in Windows Vista and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltIsVolumeWritable
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fltmgr.lib
req.dll: Fltmgr.sys
req.irql: PASSIVE_LEVEL
ms.keywords: FltIsVolumeWritable
req.iface: 
---

# FltIsVolumeWritable function



## -description
<p>The <b>FltIsVolumeWritable</b> routine determines whether the disk device that corresponds to a volume or minifilter driver instance is writable.</p>


## -syntax

````
NTSTATUS FltIsVolumeWritable(
  _In_  PVOID    FltObject,
  _Out_ PBOOLEAN IsWritable
);
````


## -parameters
<dl>

### -param <i>FltObject</i> [in]

<dd>
<p>An opaque pointer for the volume or instance. Be aware that the associated volume must be a local file system volume. </p>
</dd>

### -param <i>IsWritable</i> [out]

<dd>
<p>A pointer to a caller-allocated Boolean variable that receives <b>TRUE</b> if the volume is writable; <b>FALSE</b> otherwise. </p>
</dd>
</dl>

## -returns
<p><b>FltIsVolumeWritable</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value such as one of the following: </p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p><b>FltIsVolumeWritable</b> encountered a memory allocation failure. This is an error code.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The disk device does not support IOCTL_DISK_IS_WRITABLE requests. This is an error code.</p>

<p> </p>

## -remarks
<p><b>FltIsVolumeWritable</b> sends an <a href="https://msdn.microsoft.com/library/windows/hardware/ff560384">IOCTL_DISK_IS_WRITABLE</a> request to the underlying storage device that is associated with the given volume or instance. </p>

<p>In versions of Windows prior to Windows Vista, the <b>FltIsVolumeWritable</b> routine accepted only volumes, not instances. </p>

<p><b>FltIsVolumeWritable</b> sends an <a href="https://msdn.microsoft.com/library/windows/hardware/ff560384">IOCTL_DISK_IS_WRITABLE</a> request to the underlying storage device that is associated with the given volume or instance. </p>

<p>In versions of Windows prior to Windows Vista, the <b>FltIsVolumeWritable</b> routine accepted only volumes, not instances. </p>

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
<p>The FltIsVolumeWritable routine is available in Windows Vista and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include Fltkernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Fltmgr.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Fltmgr.sys</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560384">IOCTL_DISK_IS_WRITABLE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltIsVolumeWritable routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
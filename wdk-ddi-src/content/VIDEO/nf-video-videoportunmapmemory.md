---
UID: NF.video.VideoPortUnmapMemory
title: VideoPortUnmapMemory
author: windows-driver-content
description: The VideoPortUnmapMemory function releases a mapping between a logical address range for the adapter and a virtual address range in the user-mode address space of a particular thread. This function is the complement of VideoPortMapMemory.
old-location: display\videoportunmapmemory.htm
ms.assetid: 224c8483-56b8-4341-8347-fa119ec04024
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
req.alt-api: VideoPortUnmapMemory
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
ms.keywords: VideoPortUnmapMemory
req.iface: 
req.product: Windows 10 or later.
---

# VideoPortUnmapMemory function



## -description
<p>The <b>VideoPortUnmapMemory</b> function releases a mapping between a logical address range for the adapter and a virtual address range in the user-mode address space of a particular thread. This function is the complement of <a href="https://msdn.microsoft.com/library/windows/hardware/ff570331">VideoPortMapMemory</a>.</p>


## -syntax

````
VP_STATUS VideoPortUnmapMemory(
   PVOID  HwDeviceExtension,
   PVOID  VirtualAddress,
   HANDLE ProcessHandle
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> 

<dd>
<p>Pointer to the miniport driver's device extension.</p>
</dd>

### -param <i>VirtualAddress</i> 

<dd>
<p>Pointer to a virtual address within the mapped range to be released.</p>
</dd>

### -param <i>ProcessHandle</i> 

<dd>
<p>Should be set to zero, or to the process handle specified when the miniport driver called <b>VideoPortMapMemory</b>.</p>
</dd>
</dl>

## -returns
<p><b>VideoPortUnmapMemory</b> returns NO_ERROR if the mapping was released. Otherwise, it returns ERROR_INVALID_PARAMETER.</p>

## -remarks
<p>A miniport driver cannot release a subrange of the mapping between a logical device range and the user-space virtual address range of its corresponding display driver. Whether the <i>VirtualAddress</i> parameter is the base virtual address for the mapped range that was returned by <b>VideoPortMapMemory</b>, or is an offset into that mapped virtual range, <b>VideoPortUnmapMemory</b> releases the mapping for the full range. </p>

<p>A miniport driver cannot release a subrange of the mapping between a logical device range and the user-space virtual address range of its corresponding display driver. Whether the <i>VirtualAddress</i> parameter is the base virtual address for the mapped range that was returned by <b>VideoPortMapMemory</b>, or is an offset into that mapped virtual range, <b>VideoPortUnmapMemory</b> releases the mapping for the full range. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570331">VideoPortMapMemory</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20VideoPortUnmapMemory function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
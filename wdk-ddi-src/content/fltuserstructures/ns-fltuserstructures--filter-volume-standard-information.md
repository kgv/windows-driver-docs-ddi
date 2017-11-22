---
UID: NS.fltuserstructures._FILTER_VOLUME_STANDARD_INFORMATION
title: FILTER_VOLUME_STANDARD_INFORMATION
author: windows-driver-content
description: The caller-allocated FILTER_VOLUME_STANDARD_INFORMATION structure contains information for a volume.
old-location: ifsk\filter_volume_standard_information.htm
ms.assetid: 51f2f837-7d67-4a9d-a365-d9d1b24977e5
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltuserstructures.h
req.include-header: FltUser.h, FltKernel.h
req.target-type: Windows
req.target-min-winverclnt: This structure is available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FILTER_VOLUME_STANDARD_INFORMATION
req.alt-loc: fltuserstructures.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: FILTER_VOLUME_STANDARD_INFORMATION, FILTER_VOLUME_STANDARD_INFORMATION, *PFILTER_VOLUME_STANDARD_INFORMATION
req.iface: 
---

# FILTER_VOLUME_STANDARD_INFORMATION structure



## -description
<p>The  caller-allocated FILTER_VOLUME_STANDARD_INFORMATION structure contains information for a volume.</p>


## -syntax

````
typedef struct _FILTER_VOLUME_STANDARD_INFORMATION {
  ULONG               NextEntryOffset;
  ULONG               Flags;
  ULONG               FrameID;
  FLT_FILESYSTEM_TYPE FileSystemType;
  USHORT              FilterVolumeNameLength;
  WCHAR               FilterVolumeName[1];
} FILTER_VOLUME_STANDARD_INFORMATION, *PFILTER_VOLUME_STANDARD_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>NextEntryOffset</b>

<dd>
<p>Read-only offset, in bytes, of the next FILTER_VOLUME_STANDARD_INFORMATION structure if multiple structures are present in the buffer. This member is zero if no other structures follow this one.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>A read-only bitmask of system-defined flags that describe attributes of the volume. The following are valid flag values.</p>
<table>
<tr>
<th>Flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>FLTFL_VSI_DETACHED_VOLUME</p>
</td>
<td>
<p>The volume in not currently attached to a storage stack.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>FrameID</b>

<dd>
<p>Read-only member used to identify the filter manager frame that the volume is in.</p>
</dd>

### -field <b>FileSystemType</b>

<dd>
<p>Read-only member used to identify the type of file system being used on the volume.  The possible values for this member are listed in <a href="https://msdn.microsoft.com/library/windows/hardware/ff625876">FLT_FILESYSTEM_TYPE</a>.</p>
</dd>

### -field <b>FilterVolumeNameLength</b>

<dd>
<p>Read-only length, in bytes, of the volume name.</p>
</dd>

### -field <b>FilterVolumeName</b>

<dd>
<p>Read-only name of the volume of <b>FilterVolumeNameLength</b> length.  This Unicode string is not NULL-terminated.</p>
</dd>
</dl>

## -remarks
<p>Filter manager enumeration routines, such as <a href="https://msdn.microsoft.com/library/windows/hardware/ff542091">FltEnumerateVolumeInformation</a>, can fill a buffer with structures of type FILTER_VOLUME_STANDARD_INFORMATION where each structure represents a volume known to filter manager.  This list of structures  can contain multiple volumes with the same name.  For more information, see <a href="ifsk.understanding_volume_enumerations_with_duplicate_volume_names">Understanding Volume Enumerations with Duplicate Volume Names</a>.</p>

<p>The FILTER_VOLUME_STANDARD_INFORMATION structure must be aligned on a LONGLONG (8-byte) boundary. If a buffer contains two or more of these structures, the <b>NextEntryOffset</b> value in each entry falls on an 8-byte boundary.</p>

<p>A FILTER_VOLUME_STANDARD_INFORMATION structure can be allocated from paged or nonpaged pool.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>This structure is available starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltuserstructures.h (include FltUser.h or FltKernel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541631">FILTER_VOLUME_BASIC_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541522">FilterVolumeFindClose</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541525">FilterVolumeFindFirst</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541530">FilterVolumeFindNext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542091">FltEnumerateVolumeInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542092">FltEnumerateVolumes</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FILTER_VOLUME_STANDARD_INFORMATION structure%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
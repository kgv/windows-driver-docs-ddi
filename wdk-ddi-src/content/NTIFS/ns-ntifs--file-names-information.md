---
UID: NS.ntifs._FILE_NAMES_INFORMATION
title: FILE_NAMES_INFORMATION
author: windows-driver-content
description: A FILE_NAMES_INFORMATION structure used to query detailed information about the names of files in a directory.
old-location: ifsk\file_names_information.htm
ms.assetid: a9eb4606-fe55-4f77-914a-656ebe247066
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h, Fltkernel.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FILE_NAMES_INFORMATION
req.alt-loc: ntifs.h
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
ms.keywords: FILE_NAMES_INFORMATION, FILE_NAMES_INFORMATION, *PFILE_NAMES_INFORMATION
req.iface: 
---

# FILE_NAMES_INFORMATION structure



## -description
<p>A FILE_NAMES_INFORMATION structure used to query detailed information about the names of files in a directory. </p>


## -syntax

````
typedef struct _FILE_NAMES_INFORMATION {
  ULONG NextEntryOffset;
  ULONG FileIndex;
  ULONG FileNameLength;
  WCHAR FileName[1];
} FILE_NAMES_INFORMATION, *PFILE_NAMES_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>NextEntryOffset</b>

<dd>
<p>Byte offset for the next FILE_NAMES_INFORMATION entry, if multiple entries are present in a buffer. This member is zero if no other entries follow this one. </p>
</dd>

### -field <b>FileIndex</b>

<dd>
<p>Byte offset of the file within the parent directory. This member is undefined for file systems, such as NTFS, in which the position of a file within the parent directory is not fixed and can be changed at any time to maintain sort order. </p>
</dd>

### -field <b>FileNameLength</b>

<dd>
<p>Specifies the length of the file name string. </p>
</dd>

### -field <b>FileName</b>

<dd>
<p>Specifies the first character of the file name string. This is followed in memory by the remainder of the string. </p>
</dd>
</dl>

## -remarks
<p>This information can be queried in either of the following ways: </p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff567047">ZwQueryDirectoryFile</a>, passing FileNamesInformation as the value of <i>FileInformationClass</i> and passing a caller-allocated, FILE_NAMES_INFORMATION-structured buffer as the value of <i>FileInformation</i>. </p>

<p>Create an IRP with major function code IRP_MJ_DIRECTORY_CONTROL and minor function code IRP_MN_QUERY_DIRECTORY. </p>

<p>No specific access rights are required to query this information. </p>

<p>This structure must be aligned on a LONG (4-byte) boundary. If a buffer contains two or more of these structures, the <b>NextEntryOffset</b> value in each entry, except the last, falls on a 4-byte boundary. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h or Fltkernel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547026">FsRtlNotifyFullChangeDirectory</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548658">IRP_MJ_DIRECTORY_CONTROL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567047">ZwQueryDirectoryFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FILE_NAMES_INFORMATION structure%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
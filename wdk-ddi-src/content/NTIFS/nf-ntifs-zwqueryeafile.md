---
UID: NF.ntifs.ZwQueryEaFile
title: ZwQueryEaFile
author: windows-driver-content
description: The ZwQueryEaFile routine returns information about extended-attribute (EA) values for a file.
old-location: kernel\zwqueryeafile.htm
ms.assetid: c4261a83-3c91-4bc1-93bf-d2d04c324e94
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntifs.h
req.include-header: FltKernel.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows 2000 and later versions of the Windows operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ZwQueryEaFile
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: ZwQueryEaFile
req.iface: 
---

# ZwQueryEaFile function



## -description
<p>The <b>ZwQueryEaFile</b> routine returns 
    information about extended-attribute (EA) values for a file.</p>


## -syntax

````
NTSTATUS ZwQueryEaFile(
  _In_     HANDLE           FileHandle,
  _Out_    PIO_STATUS_BLOCK IoStatusBlock,
  _Out_    PVOID            Buffer,
  _In_     ULONG            Length,
  _In_     BOOLEAN          ReturnSingleEntry,
  _In_opt_ PVOID            EaList,
  _In_     ULONG            EaListLength,
  _In_opt_ PULONG           EaIndex,
  _In_     BOOLEAN          RestartScan
);
````


## -parameters
<dl>

### -param <i>FileHandle</i> [in]

<dd>
<p>The handle for the file on which the operation is to be performed.</p>
</dd>

### -param <i>IoStatusBlock</i> [out]

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff550671">IO_STATUS_BLOCK</a> structure that 
      receives the final completion status and other information about the requested operation.</p>
</dd>

### -param <i>Buffer</i> [out]

<dd>
<p>A pointer to a caller-supplied 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff545793">FILE_FULL_EA_INFORMATION</a>-structured output 
      buffer, where the extended attribute values are to be returned.</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>The length, in bytes, of the buffer that the <i>Buffer</i> parameter points to.</p>
</dd>

### -param <i>ReturnSingleEntry</i> [in]

<dd>
<p>Set to <b>TRUE</b> if 
      <b>ZwQueryEaFile</b> should return only the first entry that 
      is found.</p>
</dd>

### -param <i>EaList</i> [in, optional]

<dd>
<p>A pointer to a caller-supplied 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff540295">FILE_GET_EA_INFORMATION</a>-structured input 
      buffer, which specifies the extended attributes to be queried. This parameter is optional and can be 
      <b>NULL</b>.</p>
</dd>

### -param <i>EaListLength</i> [in]

<dd>
<p>The length, in bytes, of the buffer that the <i>EaList</i> parameter points to.</p>
</dd>

### -param <i>EaIndex</i> [in, optional]

<dd>
<p>The index of the entry at which scanning the file's extended-attribute list should begin. This parameter is 
      ignored if the <i>EaList</i> parameter points to a nonempty list. This parameter is optional 
      and can be <b>NULL</b>.</p>
</dd>

### -param <i>RestartScan</i> [in]

<dd>
<p>Set to <b>TRUE</b> if 
      <b>ZwQueryEaFile</b> should begin the scan at the first 
      entry in the file's extended-attribute list. If this parameter is set to <b>FALSE</b>, the 
      routine resumes the scan from a previous call to 
      <b>ZwQueryEaFile</b>.</p>
</dd>
</dl>

## -returns
<p><b>ZwQueryEaFile</b> returns 
      <b>STATUS_SUCCESS</b> or an appropriate <b>NTSTATUS</b> value such as 
      the following:</p><dl>
<dt>STATUS_EAS_NOT_SUPPORTED</dt>
</dl><p>The file system does not support extended attributes. This is an error code.</p><dl>
<dt>STATUS_INSUFFICIENT_RESOURCES</dt>
</dl><p>The <a href="https://msdn.microsoft.com/library/windows/hardware/ff961907">ZwQueryEaFile</a> routine encountered a pool 
        allocation failure. This is an error code.</p><dl>
<dt>STATUS_EA_LIST_INCONSISTENT</dt>
</dl><p>The <i>EaList</i> parameter is not formatted correctly. This is an error code.</p>

<p> </p>

## -remarks


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
<p>Available in Microsoft Windows 2000 and later versions of the Windows operating system.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include FltKernel.h or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545793">FILE_FULL_EA_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540295">FILE_GET_EA_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff961908">ZwSetEaFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ZwQueryEaFile routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
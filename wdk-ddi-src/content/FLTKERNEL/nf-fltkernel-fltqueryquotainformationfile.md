---
UID: NF.fltkernel.FltQueryQuotaInformationFile
title: FltQueryQuotaInformationFile
author: windows-driver-content
description: The FltQueryQuotaInformationFile routine retrieves quota entries associated with a file object.
old-location: ifsk\fltqueryquotainformationfile.htm
ms.assetid: B460BE83-7050-469A-9AD6-68A47F03EB4B
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with  Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltQueryQuotaInformationFile
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: PASSIVE_LEVEL
ms.keywords: FltQueryQuotaInformationFile
req.iface: 
---

# FltQueryQuotaInformationFile function



## -description
<p>The <b>FltQueryQuotaInformationFile</b> routine retrieves quota entries associated with a file object.</p>


## -syntax

````
NTSTATUS FltQueryQuotaInformationFile(
  _In_      PFLT_INSTANCE    Instance,
  _In_      PFILE_OBJECT     FileObject,
  _Out_     PIO_STATUS_BLOCK IoStatusBlock,
  _Out_     PVOID            Buffer,
  _In_      ULONG            Length,
  _In_      BOOLEAN          ReturnSingleEntry,
  _In_opt_  PVOID            SidList,
  _In_      ULONG            SidListLength,
  _In_opt_  PULONG           StartSid,
  _In_      BOOLEAN          RestartScan,
  _Out_opt_ PULONG           LengthReturned
);
````


## -parameters
<dl>

### -param <i>Instance</i> [in]

<dd>
<p>An opaque instance pointer for the caller. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>FileObject</i> [in]

<dd>
<p>A file object pointer for an open file, directory, storage device, or volume. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>IoStatusBlock</i> [out]

<dd>
<p>A caller-supplied <b>IO_STATUS_BLOCK</b> to receive the result of the call to <b>FltQueryQuotaInformationFile</b>. If the call  fails because of an invalid <b>SID</b> list, the <b>Information</b> field will contain the location in <i>SidList</i> where the error occurred.</p>
</dd>

### -param <i>Buffer</i> [out]

<dd>
<p>A pointer to a caller-supplied <a href="https://msdn.microsoft.com/2abaf505-b890-43b6-a277-d930417bdcb8"> FILE_GET_QUOTA_INFORMATION</a>-structured input buffer where the quota information values are to be returned. </p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>The length, in bytes, of the buffer that the <i>Buffer</i> parameter points to. </p>
</dd>

### -param <i>ReturnSingleEntry</i> [in]

<dd>
<p>Set to <b>TRUE</b> if <b>FltQueryQuotaInformationFile</b> should return only the first entry that is found. </p>
</dd>

### -param <i>SidList</i> [in, optional]

<dd>
<p>A pointer to a caller-supplied <a href="https://msdn.microsoft.com/library/windows/hardware/ff540298">FILE_GET_QUOTA_INFORMATION</a>-structured input buffer that specifies the quota information to be queried. This parameter is optional and can be <b>NULL</b>. </p>
</dd>

### -param <i>SidListLength</i> [in]

<dd>
<p>The length, in bytes, of the buffer that the <i>SidList</i> parameter points to. </p>
</dd>

### -param <i>StartSid</i> [in, optional]

<dd>
<p>The index of the entry at which to begin scanning the file's quota information list. This parameter is ignored if the <i>SidList</i> parameter points to a nonempty list. This parameter is optional and can be <b>NULL</b>. </p>
</dd>

### -param <i>RestartScan</i> [in]

<dd>
<p>Set to <b>TRUE</b> if <b>FltQueryQuotaInformationFile</b> should begin the scan at the first entry in the file's quota information list. If this parameter is not set to <b>TRUE</b>, the scan is resumed from a previous call to <b>FltQueryQuotaInformationFile</b>. </p>
</dd>

### -param <i>LengthReturned</i> [out, optional]

<dd>
<p>A pointer to a caller-allocated variable that receives the size, in bytes, of the information returned in <i>Buffer</i>. This parameter is optional and can be <b>NULL</b>. </p>
</dd>
</dl>

## -returns
<p><b>FltQueryQuotaInformationFile</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value such as the following. </p><dl>
<dt><b>STATUS_FLT_DELETING_OBJECT</b></dt>
</dl><p>The instance or volume is being torn down. This is an error code. </p>

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
<p>Available starting with  Windows 8.</p>
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
<dt>FltMgr.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540298">FILE_GET_QUOTA_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451042">FltSetQuotaInformationFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567064">ZwQueryQuotaInformationFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltQueryQuotaInformationFile function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
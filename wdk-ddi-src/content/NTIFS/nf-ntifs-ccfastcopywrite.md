---
UID: NF.ntifs.CcFastCopyWrite
title: CcFastCopyWrite
author: windows-driver-content
description: The CcFastCopyWrite routine performs a fast copy write from a buffer in memory to a cached file.
old-location: ifsk\ccfastcopywrite.htm
ms.assetid: 414d0b36-d7c2-4a01-8ceb-3817a11c422c
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CcFastCopyWrite
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: 
ms.keywords: CcFastCopyWrite
req.iface: 
---

# CcFastCopyWrite function



## -description
<p>The <b>CcFastCopyWrite</b> routine performs a fast copy write from a buffer in memory to a cached file.</p>


## -syntax

````
VOID CcFastCopyWrite(
  _In_ PFILE_OBJECT FileObject,
  _In_ ULONG        FileOffset,
  _In_ ULONG        Length,
  _In_ PVOID        Buffer
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>Pointer to a file object for the cached file to which the data is to be written.</p>
</dd>

### -param <i>FileOffset</i> [in]

<dd>
<p>Pointer to a variable that specifies the starting byte offset within the cached file.</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>Length in bytes of the data to be written.</p>
</dd>

### -param <i>Buffer</i> [in]

<dd>
<p>Pointer to the buffer from which the data is to be copied.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>CcFastCopyWrite</b> is a faster version of <a href="https://msdn.microsoft.com/library/windows/hardware/ff539045">CcCopyWrite</a>. It differs from <b>CcCopyWrite</b> in the following respects:</p>

<p><i>FileOffset</i> is a ULONG, not a PLARGE_INTEGER.</p>

<p>There is no <i>Wait</i> parameter. The caller must be able to enter a wait state until all the data has been copied.</p>

<p><b>CcFastCopyWrite</b> does not return a BOOLEAN to indicate whether the write operation was successful.</p>

<p>If the required pages of the cached file are already resident in memory, the data is copied immediately and no blocking occurs. If any needed pages are not resident, the caller is put in a wait state until all required pages have been made resident and the data can be copied.</p>

<p>If any failure occurs, <b>CcFastCopyWrite</b> raises a status exception for that particular failure. For example, if a pool allocation failure occurs, <b>CcFastCopyWrite</b> raises a STATUS_INSUFFICIENT_RESOURCES exception; if an I/O error occurs, <b>CcFastCopyWrite</b> raises the status exception of the I/O error. Therefore, to gain control if a failure occurs, the driver should wrap the call to <b>CcFastCopyWrite</b> in a <b>try-except</b> or <b>try-finally</b> statement.</p>

<p>To cache a file, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>.</p>

<p><b>CcFastCopyWrite</b> is a faster version of <a href="https://msdn.microsoft.com/library/windows/hardware/ff539045">CcCopyWrite</a>. It differs from <b>CcCopyWrite</b> in the following respects:</p>

<p><i>FileOffset</i> is a ULONG, not a PLARGE_INTEGER.</p>

<p>There is no <i>Wait</i> parameter. The caller must be able to enter a wait state until all the data has been copied.</p>

<p><b>CcFastCopyWrite</b> does not return a BOOLEAN to indicate whether the write operation was successful.</p>

<p>If the required pages of the cached file are already resident in memory, the data is copied immediately and no blocking occurs. If any needed pages are not resident, the caller is put in a wait state until all required pages have been made resident and the data can be copied.</p>

<p>If any failure occurs, <b>CcFastCopyWrite</b> raises a status exception for that particular failure. For example, if a pool allocation failure occurs, <b>CcFastCopyWrite</b> raises a STATUS_INSUFFICIENT_RESOURCES exception; if an I/O error occurs, <b>CcFastCopyWrite</b> raises the status exception of the I/O error. Therefore, to gain control if a failure occurs, the driver should wrap the call to <b>CcFastCopyWrite</b> in a <b>try-except</b> or <b>try-finally</b> statement.</p>

<p>To cache a file, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539045">CcCopyWrite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcFastCopyWrite routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
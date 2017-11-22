---
UID: NF.ntifs.CcWaitForCurrentLazyWriterActivity
title: CcWaitForCurrentLazyWriterActivity
author: windows-driver-content
description: The CcWaitForCurrentLazyWriterActivity routine puts the caller into a wait state until the current batch of lazy writer activity is completed.
old-location: ifsk\ccwaitforcurrentlazywriteractivity.htm
ms.assetid: eda2198d-d9c9-498a-b94f-5ebdaae417be
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available on Microsoft Windows 2000 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CcWaitForCurrentLazyWriterActivity
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
ms.keywords: CcWaitForCurrentLazyWriterActivity
req.iface: 
---

# CcWaitForCurrentLazyWriterActivity function



## -description
<p>The <b>CcWaitForCurrentLazyWriterActivity</b> routine puts the caller into a wait state until the current batch of lazy writer activity is completed.</p>


## -syntax

````
NTSTATUS CcWaitForCurrentLazyWriterActivity(void);
````


## -parameters


## -returns
<p><b>CcWaitForCurrentLazyWriterActivity</b> can return one of the following NTSTATUS values: </p><dl>
<dt>STATUS_SUCCESS</dt>
<dt>STATUS_INSUFFICIENT_RESOURCES</dt>
</dl><p><b>CcWaitForCurrentLazyWriterActivity</b> can return one of the following NTSTATUS values: </p><dl>
<dt>STATUS_SUCCESS</dt>
<dt>STATUS_INSUFFICIENT_RESOURCES</dt>
</dl><p><b>CcWaitForCurrentLazyWriterActivity</b> can return one of the following NTSTATUS values: </p><dl>
<dt>STATUS_SUCCESS</dt>
<dt>STATUS_INSUFFICIENT_RESOURCES</dt>
</dl>

## -remarks
<p><b>CcWaitForCurrentLazyWriterActivity</b> puts the calling thread into a wait state until all work items currently in the lazy writer (read ahead or write behind) work queue have completed.</p>

<p>To prevent deadlock, the caller should release any currently held synchronization objects before calling <b>CcWaitForCurrentLazyWriterActivity</b>.</p>

<p><b>CcWaitForCurrentLazyWriterActivity</b> puts the calling thread into a wait state until all work items currently in the lazy writer (read ahead or write behind) work queue have completed.</p>

<p>To prevent deadlock, the caller should release any currently held synchronization objects before calling <b>CcWaitForCurrentLazyWriterActivity</b>.</p>

<p><b>CcWaitForCurrentLazyWriterActivity</b> puts the calling thread into a wait state until all work items currently in the lazy writer (read ahead or write behind) work queue have completed.</p>

<p>To prevent deadlock, the caller should release any currently held synchronization objects before calling <b>CcWaitForCurrentLazyWriterActivity</b>.</p>

<p><b>CcWaitForCurrentLazyWriterActivity</b> puts the calling thread into a wait state until all work items currently in the lazy writer (read ahead or write behind) work queue have completed.</p>

<p>To prevent deadlock, the caller should release any currently held synchronization objects before calling <b>CcWaitForCurrentLazyWriterActivity</b>.</p>

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
<p>Available on Microsoft Windows 2000 and later. </p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539191">CcReadAhead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539203">CcSetAdditionalCacheAttributes</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539224">CcSetReadAheadGranularity</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcWaitForCurrentLazyWriterActivity routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
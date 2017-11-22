---
UID: NF.ntifs.ZwFreeVirtualMemory
title: ZwFreeVirtualMemory
author: windows-driver-content
description: The ZwFreeVirtualMemory routine releases, decommits, or both, a region of pages within the virtual address space of a specified process.
old-location: kernel\zwfreevirtualmemory.htm
ms.assetid: ca6675cf-3482-4e62-8f7c-801c1deacd37
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntifs.h
req.include-header: Ntifs.h, Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ZwFreeVirtualMemory,NtFreeVirtualMemory
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
ms.keywords: ZwFreeVirtualMemory
req.iface: 
---

# ZwFreeVirtualMemory function



## -description
<p>The <b>ZwFreeVirtualMemory</b> routine releases, decommits, or both, a region of pages within the virtual address space of a specified process.</p>


## -syntax

````
NTSTATUS ZwFreeVirtualMemory(
  _In_    HANDLE  ProcessHandle,
  _Inout_ PVOID   *BaseAddress,
  _Inout_ PSIZE_T RegionSize,
  _In_    ULONG   FreeType
);
````


## -parameters
<dl>

### -param <i>ProcessHandle</i> [in]

<dd>
<p>A handle for the process in whose context the pages to be freed reside. Use the <b>NtCurrentProcess</b> macro, defined in Ntddk.h, to specify the current process.</p>
</dd>

### -param <i>BaseAddress</i> [in, out]

<dd>
<p>A pointer to a variable that will receive the virtual address of the freed region of pages. </p>
<p>If the MEM_RELEASE flag is set in the <i>FreeType</i> parameter, <i>BaseAddress</i> must be the base address returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a> when the region was reserved.</p>
</dd>

### -param <i>RegionSize</i> [in, out]

<dd>
<p>A pointer to a variable that will receive the actual size, in bytes, of the freed region of pages. The routine rounds the initial value of this variable up to the next host page size boundary and writes the rounded value back to this variable.</p>
<p>If the MEM_RELEASE flag is set in the <i>FreeType</i> parameter, the variable pointed to by <i>RegionSize</i> must be zero. <b>ZwFreeVirtualMemory</b> frees the entire region that was reserved in the initial allocation call to <b>ZwAllocateVirtualMemory</b>.</p>
<p>If the MEM_DECOMMIT flag is set in the <i>FreeType</i> parameter, <b>ZwFreeVirtualMemory</b> decommits all memory pages that contain one or more bytes in the range from the <i>BaseAddress</i> parameter to (<i>BaseAddress</i> + *<i>RegionSize</i>). This means, for example, that if a two-byte region of memory straddles a page boundary, both pages are decommitted.</p>
<p><b>ZwFreeVirtualMemory</b> decommits the entire region that was reserved by <b>ZwAllocateVirtualMemory</b>. If the following three conditions are met, the entire region enters the reserved state:</p>
<ul>
<li>
<p>The MEM_DECOMMIT flag is set.</p>
</li>
<li>
<p><i>BaseAddress</i> is the base address returned by <b>ZwAllocateVirtualMemory</b> when the region was reserved.</p>
</li>
<li>
<p>
         *<i>RegionSize</i> is zero.</p>
</li>
</ul>
</dd>

### -param <i>FreeType</i> [in]

<dd>
<p>A bitmask that contains flags that describe the type of free operation that <b>ZwFreeVirtualMemory</b> will perform for the specified region of pages. The possible values are listed in the following table.</p>
<table>
<tr>
<th><i>FreeType</i> flags</th>
<th>Description</th>
</tr>
<tr>
<td>
<p>MEM_DECOMMIT</p>
</td>
<td>
<p><b>ZwFreeVirtualMemory</b> will decommit the specified region of pages. The pages enter the reserved state.</p>
<p><b>ZwFreeVirtualMemory</b> does not fail if you attempt to decommit an uncommitted page. This means that you can decommit a range of pages without first determining their current commitment state.</p>
</td>
</tr>
<tr>
<td>
<p>MEM_RELEASE</p>
</td>
<td>
<p><b>ZwFreeVirtualMemory</b> will release the specified region of pages. The pages enter the free state.</p>
<p>If you specify this flag, *<i>RegionSize</i> must be zero, and <i>BaseAddress </i>must point to the base address returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a> when the region was reserved. <b>ZwFreeVirtualMemory</b> fails if either of these conditions is not met.</p>
<p>If any pages in the region are currently committed, <b>ZwFreeVirtualMemory</b> first decommits and then releases them.</p>
<p><b>ZwFreeVirtualMemory</b> does not fail if you attempt to release pages that are in different states, some reserved and some committed. This means that you can release a range of pages without first determining their current commitment state.</p>
</td>
</tr>
</table>
<p> </p>
</dd>
</dl>

## -returns
<p><b>ZwFreeVirtualMemory</b> returns either STATUS_SUCCESS or an error status code. Possible error status codes include the following.</p><dl>
<dt><b>STATUS_ACCESS_DENIED</b></dt>
</dl><p>A process has requested access to an object, but has not been granted those access rights.</p><dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><p>An invalid <i>ProcessHandle</i> value was specified.</p><dl>
<dt><b>STATUS_OBJECT_TYPE_MISMATCH</b></dt>
</dl><p>There is a mismatch between the type of object required by the requested operation and the type of object that is specified in the request.</p>

<p> </p>

## -remarks
<p>Each page in the process's virtual address space is in one of the three states described in the following table.</p>

<p>FREE</p>

<p>The page is neither committed nor reserved. The page is not accessible to the process. Attempting to read from or write to a free page results in an access violation exception. </p>

<p>You can use <b>ZwFreeVirtualMemory</b> to put reserved or committed pages into the free state.</p>

<p>RESERVED</p>

<p>The page is reserved. The range of addresses cannot be used by other allocation functions. The page is not accessible to the process and has no physical storage associated with it. Attempting to read from or write to a reserved page results in an access violation exception. </p>

<p>You can use <b>ZwFreeVirtualMemory</b> to put committed memory pages into the reserved state, and to put reserved memory pages into the free state. </p>

<p>COMMITTED</p>

<p>The page is committed. Physical storage in memory or in the paging file on disk is allocated for the page, and access is controlled by a protection code. </p>

<p>The system initializes and loads each committed page into physical memory only at the first attempt to read from or write to that page. </p>

<p>When a process terminates, the system releases all storage for committed pages.</p>

<p>You can use <a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a> to put committed memory pages into either the reserved or free state.</p>

<p> </p>

<p><b>ZwFreeVirtualMemory</b> can perform the following operations:</p>

<p>Decommit a region of committed or uncommitted pages. After this operation, the pages are in the reserved state. </p>

<p>Release a region of reserved pages. After this operation, the pages are in the free state.</p>

<p>Decommit and release a region of committed or uncommitted pages. After this operation, the pages are in the free state. </p>

<p><b>ZwFreeVirtualMemory</b> can decommit a range of pages that are in different states, some committed and some uncommitted. This means that you can decommit a range of pages without first determining the current commitment state of each page. Decommitting a page releases its physical storage, either in memory or in the paging file on disk.</p>

<p>If a page is decommitted but not released, its state changes to reserved. You can subsequently call <b>ZwAllocateVirtualMemory</b> to commit it, or <b>ZwFreeVirtualMemory</b> to release it. Attempting to read from or write to a reserved page results in an access violation exception.</p>

<p><b>ZwFreeVirtualMemory</b> can release a range of pages that are in different states, some reserved and some committed. This means that you can release a range of pages without first determining the current commitment state of each page. The entire range of pages originally reserved by <a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a> must be released at the same time.</p>

<p>If a page is released, its state changes to free, and it is available for subsequent allocation operations. After memory has been released or decommitted, you can never refer to the memory again. Any information that may have been in that memory is gone forever. Attempting to read from or write to a free page results in an access violation exception. If you require information, do not decommit or free memory that contains that information.</p>

<p>For more information about memory management support for kernel-mode drivers, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554389">Memory Management for Windows Drivers</a>.</p>

<p>For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.</p>

<p>Each page in the process's virtual address space is in one of the three states described in the following table.</p>

<p>FREE</p>

<p>The page is neither committed nor reserved. The page is not accessible to the process. Attempting to read from or write to a free page results in an access violation exception. </p>

<p>You can use <b>ZwFreeVirtualMemory</b> to put reserved or committed pages into the free state.</p>

<p>RESERVED</p>

<p>The page is reserved. The range of addresses cannot be used by other allocation functions. The page is not accessible to the process and has no physical storage associated with it. Attempting to read from or write to a reserved page results in an access violation exception. </p>

<p>You can use <b>ZwFreeVirtualMemory</b> to put committed memory pages into the reserved state, and to put reserved memory pages into the free state. </p>

<p>COMMITTED</p>

<p>The page is committed. Physical storage in memory or in the paging file on disk is allocated for the page, and access is controlled by a protection code. </p>

<p>The system initializes and loads each committed page into physical memory only at the first attempt to read from or write to that page. </p>

<p>When a process terminates, the system releases all storage for committed pages.</p>

<p>You can use <a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a> to put committed memory pages into either the reserved or free state.</p>

<p> </p>

<p><b>ZwFreeVirtualMemory</b> can perform the following operations:</p>

<p>Decommit a region of committed or uncommitted pages. After this operation, the pages are in the reserved state. </p>

<p>Release a region of reserved pages. After this operation, the pages are in the free state.</p>

<p>Decommit and release a region of committed or uncommitted pages. After this operation, the pages are in the free state. </p>

<p><b>ZwFreeVirtualMemory</b> can decommit a range of pages that are in different states, some committed and some uncommitted. This means that you can decommit a range of pages without first determining the current commitment state of each page. Decommitting a page releases its physical storage, either in memory or in the paging file on disk.</p>

<p>If a page is decommitted but not released, its state changes to reserved. You can subsequently call <b>ZwAllocateVirtualMemory</b> to commit it, or <b>ZwFreeVirtualMemory</b> to release it. Attempting to read from or write to a reserved page results in an access violation exception.</p>

<p><b>ZwFreeVirtualMemory</b> can release a range of pages that are in different states, some reserved and some committed. This means that you can release a range of pages without first determining the current commitment state of each page. The entire range of pages originally reserved by <a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a> must be released at the same time.</p>

<p>If a page is released, its state changes to free, and it is available for subsequent allocation operations. After memory has been released or decommitted, you can never refer to the memory again. Any information that may have been in that memory is gone forever. Attempting to read from or write to a free page results in an access violation exception. If you require information, do not decommit or free memory that contains that information.</p>

<p>For more information about memory management support for kernel-mode drivers, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554389">Memory Management for Windows Drivers</a>.</p>

<p>For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.</p>

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
<p>Available starting with Windows 2000.</p>
</td>
</tr>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566416">ZwAllocateVirtualMemory</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ZwFreeVirtualMemory routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
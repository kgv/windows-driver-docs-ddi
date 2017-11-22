---
UID: NF.ntifs.KeInsertQueue
title: KeInsertQueue
author: windows-driver-content
description: The KeInsertQueue routine inserts an entry at the tail of the given queue if it cannot immediately use the entry to satisfy a thread wait.
old-location: ifsk\keinsertqueue.htm
ms.assetid: 0aee6102-e9e3-41dc-a222-36bebb3d4294
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
req.alt-api: KeInsertQueue
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
req.irql: <= DISPATCH_LEVEL
ms.keywords: KeInsertQueue
req.iface: 
---

# KeInsertQueue function



## -description
<p>The <b>KeInsertQueue</b> routine inserts an entry at the tail of the given queue if it cannot immediately use the entry to satisfy a thread wait. </p>


## -syntax

````
LONG KeInsertQueue(
  _Inout_ PRKQUEUE    Queue,
  _Inout_ PLIST_ENTRY Entry
);
````


## -parameters
<dl>

### -param <i>Queue</i> [in, out]

<dd>
<p>Pointer to an initialized queue object for which the caller provides resident storage in nonpaged pool. </p>
</dd>

### -param <i>Entry</i> [in, out]

<dd>
<p>Pointer to an entry to be queued. This pointer must be a resident system-space address. </p>
</dd>
</dl>

## -returns
<p><b>KeInsertQueue</b> returns the previous signal state of the given <i>Queue</i>. If it was set to zero (that is, not signaled) before <b>KeInsertQueue</b> was called, <b>KeInsertQueue</b> returns zero, meaning that no entries were queued. If it was nonzero (signaled), <b>KeInsertQueue</b> returns the number of entries that were queued before <b>KeInsertQueue</b> was called. </p>

## -remarks
<p>Entries to be queued by <b>KeInsertQueue</b> must be allocated from nonpaged pool. For example, memory for caller-defined entries can be allocated with <a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a>. If the caller allocates entries of a fixed size, creating a lookaside list with <a href="https://msdn.microsoft.com/library/windows/hardware/ff545301">ExInitializeNPagedLookasideList</a> and allocating from it with <a href="https://msdn.microsoft.com/library/windows/hardware/ff544388">ExAllocateFromNPagedLookasideList</a> is more efficient than making frequent calls to <b>ExAllocatePoolWithTag</b>, particularly for entries whose size is not a multiple of PAGE_SIZE. </p>

<p>If any threads are waiting on the queue object when <b>KeInsertQueue</b> is called, a single thread's wait is satisfied by this call. The thread is dispatched for execution with the given <i>Entry</i> pointer. </p>

<p>If no threads are currently waiting on the queue object when <b>KeInsertQueue</b> is called, the given entry is inserted in the queue, and the queue object's signal state is incremented. </p>

<p>For more information about using driver-managed internal queues, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544165">Driver-Managed Queues</a>. </p>

<p>Entries to be queued by <b>KeInsertQueue</b> must be allocated from nonpaged pool. For example, memory for caller-defined entries can be allocated with <a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a>. If the caller allocates entries of a fixed size, creating a lookaside list with <a href="https://msdn.microsoft.com/library/windows/hardware/ff545301">ExInitializeNPagedLookasideList</a> and allocating from it with <a href="https://msdn.microsoft.com/library/windows/hardware/ff544388">ExAllocateFromNPagedLookasideList</a> is more efficient than making frequent calls to <b>ExAllocatePoolWithTag</b>, particularly for entries whose size is not a multiple of PAGE_SIZE. </p>

<p>If any threads are waiting on the queue object when <b>KeInsertQueue</b> is called, a single thread's wait is satisfied by this call. The thread is dispatched for execution with the given <i>Entry</i> pointer. </p>

<p>If no threads are currently waiting on the queue object when <b>KeInsertQueue</b> is called, the given entry is inserted in the queue, and the queue object's signal state is incremented. </p>

<p>For more information about using driver-managed internal queues, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544165">Driver-Managed Queues</a>. </p>

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
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544388">ExAllocateFromNPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545301">ExInitializeNPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549547">KeInitializeQueue</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549559">KeInsertHeadQueue</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549605">KeRemoveQueue</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20KeInsertQueue routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
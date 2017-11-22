---
UID: NF.wdm.RemoveEntryList~r1
title: RemoveEntryList
author: windows-driver-content
description: The RemoveEntryList routine removes an entry from a doubly linked list of LIST_ENTRY structures.
old-location: kernel\removeentrylist.htm
ms.assetid: 84c3937f-8042-4b15-b5bb-884d14a97a8c
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RemoveEntryList
req.alt-loc: Wdm.h
req.ddi-compliance: DoubleExFreePool
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level (See Remarks section)
ms.keywords: RemoveEntryList
req.iface: 
req.product: Windows 10 or later.
---

# RemoveEntryList function



## -description
<p>The <b>RemoveEntryList</b> routine removes an entry from a doubly linked list of <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structures.</p>


## -syntax

````
BOOLEAN RemoveEntryList(
  _In_ PLIST_ENTRY Entry
);
````


## -parameters
<dl>

### -param <i>Entry</i> [in]

<dd>
<p>Pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure that represents the entry to be removed.</p>
</dd>
</dl>

## -returns
<p><b>RemoveEntryList</b> returns <b>TRUE</b> if, after removal of the designated entry, the list is empty. Otherwise, the routine returns <b>FALSE</b> to indicate that the resulting list still contains one or more entries. For information, see Remarks.</p>

## -remarks
<p><b>RemoveEntryList</b> removes the entry by setting the <b>Flink</b> member of the entry before <i>Entry</i> to point to the entry after <i>Entry</i>, and the <b>Blink</b> member of the entry after <i>Entry</i> to point to the entry before <i>Entry</i>.</p>

<p>The return value can be used to detect when the last entry is removed from the list. An empty list consists of a list head only and no list entries.</p>

<p>For information about using this routine when implementing a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.</p>

<p>In Windows XP and Windows 2000, <b>RemoveEntryList</b> did not return a value. Starting with Windows Server 2003, <b>RemoveEntryList</b> returns a BOOLEAN value.</p>

<p>Callers of <b>RemoveEntryList</b> can be running at any IRQL. If <b>RemoveEntryList</b> is called at IRQL &gt;= DISPATCH_LEVEL, the storage for the list entries must be resident.</p>

<p><b>RemoveEntryList</b> removes the entry by setting the <b>Flink</b> member of the entry before <i>Entry</i> to point to the entry after <i>Entry</i>, and the <b>Blink</b> member of the entry after <i>Entry</i> to point to the entry before <i>Entry</i>.</p>

<p>The return value can be used to detect when the last entry is removed from the list. An empty list consists of a list head only and no list entries.</p>

<p>For information about using this routine when implementing a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.</p>

<p>In Windows XP and Windows 2000, <b>RemoveEntryList</b> did not return a value. Starting with Windows Server 2003, <b>RemoveEntryList</b> returns a BOOLEAN value.</p>

<p>Callers of <b>RemoveEntryList</b> can be running at any IRQL. If <b>RemoveEntryList</b> is called at IRQL &gt;= DISPATCH_LEVEL, the storage for the list entries must be resident.</p>

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
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level (See Remarks section)</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454214">DoubleExFreePool</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547799">InitializeListHead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551789">IsListEmpty</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561032">RemoveHeadList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561036">RemoveTailList</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RemoveEntryList routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
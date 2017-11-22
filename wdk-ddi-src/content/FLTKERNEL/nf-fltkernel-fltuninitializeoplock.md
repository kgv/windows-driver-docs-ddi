---
UID: NF.fltkernel.FltUninitializeOplock
title: FltUninitializeOplock
author: windows-driver-content
description: FltUninitializeOplock uninitializes an opportunistic lock (oplock) pointer.
old-location: ifsk\fltuninitializeoplock.htm
ms.assetid: 6379014a-f9bc-4e86-93da-83d90f009a3b
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltUninitializeOplock
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
req.irql: <= APC_LEVEL
ms.keywords: FltUninitializeOplock
req.iface: 
---

# FltUninitializeOplock function



## -description
<p><b>FltUninitializeOplock</b> uninitializes an opportunistic lock (oplock) pointer. </p>


## -syntax

````
VOID FltUninitializeOplock(
  _In_ POPLOCK Oplock
);
````


## -parameters
<dl>

### -param <i>Oplock</i> [in]

<dd>
<p>Opaque oplock pointer. This pointer must have been initialized by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>. </p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p>Minifilter drivers call <b>FltUninitializeOplock</b> to uninitialize an initialized opportunistic lock (oplock) pointer. The uninitialized oplock pointer can be initialized for reuse by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>. </p>

<p>For detailed information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

<p>Minifilter drivers call <b>FltUninitializeOplock</b> to uninitialize an initialized opportunistic lock (oplock) pointer. The uninitialized oplock pointer can be initialized for reuse by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>. </p>

<p>For detailed information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541844">FltCheckOplock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541946">FltCurrentBatchOplock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543398">FltOplockFsctrl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543404">FltOplockIsFastIoPossible</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545462">FSCTL_OPBATCH_ACK_CLOSE_PENDING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545476">FSCTL_OPLOCK_BREAK_ACK_NO_2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545468">FSCTL_OPLOCK_BREAK_ACKNOWLEDGE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545485">FSCTL_OPLOCK_BREAK_NOTIFY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545510">FSCTL_REQUEST_BATCH_OPLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545518">FSCTL_REQUEST_FILTER_OPLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545538">FSCTL_REQUEST_OPLOCK_LEVEL_1</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545546">FSCTL_REQUEST_OPLOCK_LEVEL_2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547328">FsRtlUninitializeOplock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltUninitializeOplock function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
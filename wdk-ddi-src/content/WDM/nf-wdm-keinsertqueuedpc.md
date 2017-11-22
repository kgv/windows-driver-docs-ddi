---
UID: NF.wdm.KeInsertQueueDpc
title: KeInsertQueueDpc
author: windows-driver-content
description: The KeInsertQueueDpc routine queues a DPC for execution.
old-location: kernel\keinsertqueuedpc.htm
ms.assetid: f1fc6880-23d1-4154-9305-4a918efd4a1d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeInsertQueueDpc
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: MarkingQueuedIrps, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level
ms.keywords: KeInsertQueueDpc
req.iface: 
req.product: Windows 10 or later.
---

# KeInsertQueueDpc function



## -description
<p>The <b>KeInsertQueueDpc</b> routine queues a DPC for execution. </p>


## -syntax

````
BOOLEAN KeInsertQueueDpc(
  _Inout_  PRKDPC Dpc,
  _In_opt_ PVOID  SystemArgument1,
  _In_opt_ PVOID  SystemArgument2
);
````


## -parameters
<dl>

### -param <i>Dpc</i> [in, out]

<dd>
<p>Pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551882">KDPC</a> structure for the DPC object. This structure must have been initialized by either <a href="https://msdn.microsoft.com/library/windows/hardware/ff552130">KeInitializeDpc</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff552166">KeInitializeThreadedDpc</a>.</p>
</dd>

### -param <i>SystemArgument1</i> [in, optional]

<dd>
<p>Specifies driver-determined context data. This value is passed as the <i>SystemArgument1</i> parameter to the DPC object's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542972">CustomDpc</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff542976">CustomThreadedDpc</a> routine. </p>
</dd>

### -param <i>SystemArgument2</i> [in, optional]

<dd>
<p>Specifies driver-determined context data. This value is passed as the <i>SystemArgument2</i> parameter to the DPC object's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542972">CustomDpc</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff542976">CustomThreadedDpc</a> routine. </p>
</dd>
</dl>

## -returns
<p>If the specified DPC object is not currently in a DPC queue, <b>KeInsertQueueDpc</b> queues the DPC and returns <b>TRUE</b>.</p>

## -remarks
<p>If the specified DPC object has already been queued, no operation is performed except to return <b>FALSE</b>. Otherwise, the DPC object is inserted in a DPC queue. For more information about DPC queues, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff558754">Organization of DPC Queues</a>.</p>

<p>Note that a particular DPC object and the function that it represents can each be queued for execution only once at any particular time. </p>

<p>If the specified DPC object has already been queued, no operation is performed except to return <b>FALSE</b>. Otherwise, the DPC object is inserted in a DPC queue. For more information about DPC queues, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff558754">Organization of DPC Queues</a>.</p>

<p>Note that a particular DPC object and the function that it represents can each be queued for execution only once at any particular time. </p>

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
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
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
<p>Any level</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549016">MarkingQueuedIrps</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542972">CustomDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542976">CustomThreadedDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552130">KeInitializeDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553169">KeRemoveQueueDpc</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeInsertQueueDpc routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
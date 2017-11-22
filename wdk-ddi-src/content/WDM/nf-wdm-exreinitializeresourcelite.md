---
UID: NF.wdm.ExReinitializeResourceLite
title: ExReinitializeResourceLite
author: windows-driver-content
description: The ExReinitializeResourceLite routine reinitializes an existing resource variable.
old-location: kernel\exreinitializeresourcelite.htm
ms.assetid: 5713edfd-0b73-4274-862d-23c97f991a68
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
req.alt-api: ExReinitializeResourceLite
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL
ms.keywords: ExReinitializeResourceLite
req.iface: 
req.product: Windows 10 or later.
---

# ExReinitializeResourceLite function



## -description
<p>The <b>ExReinitializeResourceLite</b> routine reinitializes an existing resource variable.</p>


## -syntax

````
NTSTATUS ExReinitializeResourceLite(
  _Inout_ PERESOURCE Resource
);
````


## -parameters
<dl>

### -param <i>Resource</i> [in, out]

<dd>
<p>A pointer to the caller-supplied resource variable to be reinitialized.</p>
</dd>
</dl>

## -returns
<p><b>ExReinitializeResourceLite</b> returns STATUS_SUCCESS.</p>

## -remarks
<p>With a single call to <b>ExReinitializeResource</b>, a driver writer can replace three calls: one to <b>ExDeleteResourceLite</b>, another to <b>ExAllocatePool</b>, and a third to <b>ExInitializeResourceLite</b>. As contention for a resource variable increases, memory is dynamically allocated and attached to the resource in order to track this contention. As an optimization, <b>ExReinitializeResourceLite</b> retains and zeros this previously allocated memory.</p>

<p>The <b>ERESOURCE</b> structure is opaque; that is, the members are reserved for system use.</p>

<p>With a single call to <b>ExReinitializeResource</b>, a driver writer can replace three calls: one to <b>ExDeleteResourceLite</b>, another to <b>ExAllocatePool</b>, and a third to <b>ExInitializeResourceLite</b>. As contention for a resource variable increases, memory is dynamically allocated and attached to the resource in order to track this contention. As an optimization, <b>ExReinitializeResourceLite</b> retains and zeros this previously allocated memory.</p>

<p>The <b>ERESOURCE</b> structure is opaque; that is, the members are reserved for system use.</p>

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544351">ExAcquireResourceExclusiveLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544363">ExAcquireResourceSharedLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545317">ExInitializeResourceLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544578">ExDeleteResourceLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544367">ExAcquireSharedStarveExclusive</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544370">ExAcquireSharedWaitForExclusive</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544558">ExConvertExclusiveToSharedLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545458">ExIsResourceAcquiredExclusiveLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545477">ExIsResourceAcquiredSharedLite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545585">ExReleaseResourceForThreadLite</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ExReinitializeResourceLite routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
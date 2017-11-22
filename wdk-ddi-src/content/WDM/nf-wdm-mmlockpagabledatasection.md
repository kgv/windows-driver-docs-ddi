---
UID: NF.wdm.MmLockPagableDataSection
title: MmLockPagableDataSection
author: windows-driver-content
description: The MmLockPagableDataSection routine locks an entire section of driver data into system space.
old-location: kernel\mmlockpagabledatasection.htm
ms.assetid: 9bf21128-acf3-4d7d-83c5-a32ac54e78ca
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
req.alt-api: MmLockPagableDataSection
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlMmApcLte, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <=APC_LEVEL
ms.keywords: MmLockPagableDataSection
req.iface: 
req.product: Windows 10 or later.
---

# MmLockPagableDataSection function



## -description
<p>The <b>MmLockPagableDataSection</b> routine locks an entire section of driver data into system space.</p>


## -syntax

````
PVOID MmLockPagableDataSection(
  _In_ PVOID AddressWithinSection
);
````


## -parameters
<dl>

### -param <i>AddressWithinSection</i> [in]

<dd>
<p>Specifies the symbolic address of one item of data within the pageable section.</p>
</dd>
</dl>

## -returns
<p><b>MmLockPagableDataSection</b> returns an opaque value that identifies the section. This value must be passed subsequently to <b>MmLockPagableSectionByHandle</b> or to <b>MmUnlockPagableImageSection</b>.</p>

## -remarks
<p>Drivers can use this routine, <b>MmLockPagableSectionByHandle</b>, and <b>MmUnlockPagableImageSection</b> to make their private data that is typically pageable locked into memory.</p>

<p>Data can be locked down if:</p>

<p>The data is typically accessed at &lt;= APC_LEVEL, but it might need to be accessed at higher IRQL levels for short periods. </p>

<p>The driver uses the data infrequently and predictably. </p>

<p>For example, drivers for mixer devices use pageable-data sections. Because the driver uses sufficient data to make creating a pageable-data section worthwhile and the driver knows when the data is needed, such a driver uses <b>MmLockPagableDataSection</b>,  <b>MmLockPagableSectionByHandle</b> and <b>MmUnlockPagableImageSection</b> to bring a data section into system space when needed and make it available to be paged out when not needed.</p>

<p>A single call to <b>MmLockPagableDataSection</b> causes the entire section, containing the referenced data, to be locked into system space.</p>

<p>It is an expensive operation to lock down a section. If a pageable-data section is locked down in more than one place by a driver, use <b>MmLockPagableDataSection</b> for the first request. Make subsequent lock requests by calling <b>MmLockPagableSectionByHandle</b>, passing the handle returned by <b>MmLockPagableDataSection</b>. Locking by handle significantly improves driver performance. A locked down section is unlocked by calling <b>MmUnlockPagableImageSection</b>.</p>

<p>The memory manager maintains a reference count on the section. A pageable-data section is only available to be paged out when the reference count is zero. Every lock request increments the count; every unlock request decrements the count. A driver must unlock a section as many times as it locks a section to ensure that such a section will be available to be paged out when the section is not needed. A handle is always valid, no matter what the count. If the count on a handle is zero and a call is made to <b>MmLockPagableSectionByHandle</b>, the count is set to one, and if the section has been paged out, it will be paged in.</p>

<p>Data in a pageable-data section is marked by a compiler directive. To create a pageable data section, use <b>#pragma data_seg ("PAGE")</b>, at the beginning of the data module, and <b>#pragma data_seg ()</b> at the end of the module. The keyword <b>PAGE</b> is case-sensitive, that is, <b>PAGE</b> must be capitalized.</p>

<p>Note that there is also a <b>#pragma data_seg("INIT")</b> that is used to make data discardable after system initialization. Except for the use of <b>INIT</b> rather than <b>PAGE</b>, the syntax is the same. However the result is not; use of the <b>PAGE</b> directive makes the data section pageable. When the <b>INIT</b> directive is used, the data in the section is discarded as soon as the driver returns from its driver entry routine or its reinitialization routine if the driver has one.</p>

<p>For more information about paging data, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554346">Making Drivers Pageable</a>. </p>

<p>Drivers can use this routine, <b>MmLockPagableSectionByHandle</b>, and <b>MmUnlockPagableImageSection</b> to make their private data that is typically pageable locked into memory.</p>

<p>Data can be locked down if:</p>

<p>The data is typically accessed at &lt;= APC_LEVEL, but it might need to be accessed at higher IRQL levels for short periods. </p>

<p>The driver uses the data infrequently and predictably. </p>

<p>For example, drivers for mixer devices use pageable-data sections. Because the driver uses sufficient data to make creating a pageable-data section worthwhile and the driver knows when the data is needed, such a driver uses <b>MmLockPagableDataSection</b>,  <b>MmLockPagableSectionByHandle</b> and <b>MmUnlockPagableImageSection</b> to bring a data section into system space when needed and make it available to be paged out when not needed.</p>

<p>A single call to <b>MmLockPagableDataSection</b> causes the entire section, containing the referenced data, to be locked into system space.</p>

<p>It is an expensive operation to lock down a section. If a pageable-data section is locked down in more than one place by a driver, use <b>MmLockPagableDataSection</b> for the first request. Make subsequent lock requests by calling <b>MmLockPagableSectionByHandle</b>, passing the handle returned by <b>MmLockPagableDataSection</b>. Locking by handle significantly improves driver performance. A locked down section is unlocked by calling <b>MmUnlockPagableImageSection</b>.</p>

<p>The memory manager maintains a reference count on the section. A pageable-data section is only available to be paged out when the reference count is zero. Every lock request increments the count; every unlock request decrements the count. A driver must unlock a section as many times as it locks a section to ensure that such a section will be available to be paged out when the section is not needed. A handle is always valid, no matter what the count. If the count on a handle is zero and a call is made to <b>MmLockPagableSectionByHandle</b>, the count is set to one, and if the section has been paged out, it will be paged in.</p>

<p>Data in a pageable-data section is marked by a compiler directive. To create a pageable data section, use <b>#pragma data_seg ("PAGE")</b>, at the beginning of the data module, and <b>#pragma data_seg ()</b> at the end of the module. The keyword <b>PAGE</b> is case-sensitive, that is, <b>PAGE</b> must be capitalized.</p>

<p>Note that there is also a <b>#pragma data_seg("INIT")</b> that is used to make data discardable after system initialization. Except for the use of <b>INIT</b> rather than <b>PAGE</b>, the syntax is the same. However the result is not; use of the <b>PAGE</b> directive makes the data section pageable. When the <b>INIT</b> directive is used, the data in the section is discarded as soon as the driver returns from its driver entry routine or its reinitialization routine if the driver has one.</p>

<p>For more information about paging data, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554346">Making Drivers Pageable</a>. </p>

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
<p>&lt;=APC_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/075f5710-b2bf-4546-9648-661a3c8521f8">IrqlMmApcLte</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554601">MmLockPagableCodeSection</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554610">MmLockPagableSectionByHandle</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554650">MmPageEntireDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554680">MmResetDriverPaging</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556377">MmUnlockPagableImageSection</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20MmLockPagableDataSection routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
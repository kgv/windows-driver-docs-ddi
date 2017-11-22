---
UID: NF.wdm.ExInterlockedAddUlong
title: ExInterlockedAddUlong
author: windows-driver-content
description: The ExInterlockedAddUlong routine adds an unsigned long value to a given unsigned integer as an atomic operation.
old-location: kernel\exinterlockedaddulong.htm
ms.assetid: c418538a-4041-4ea8-8a4c-1f4d35e434c7
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
req.alt-api: ExInterlockedAddUlong
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
req.irql: Any level (see Remarks section)
ms.keywords: ExInterlockedAddUlong
req.iface: 
req.product: Windows 10 or later.
---

# ExInterlockedAddUlong function



## -description
<p>The <b>ExInterlockedAddUlong</b> routine adds an unsigned long value to a given unsigned integer as an atomic operation.</p>


## -syntax

````
ULONG ExInterlockedAddUlong(
  _Inout_ PULONG      Addend,
  _In_    ULONG       Increment,
  _Inout_ PKSPIN_LOCK Lock
);
````


## -parameters
<dl>

### -param <i>Addend</i> [in, out]

<dd>
<p>A pointer to an unsigned long integer whose value is to be adjusted by the <i>Increment</i> value.</p>
</dd>

### -param <i>Increment</i> [in]

<dd>
<p>Specifies an unsigned long integer to be added. </p>
</dd>

### -param <i>Lock</i> [in, out]

<dd>
<p>A pointer to a spin lock to be used to synchronize access to the <i>Addend</i>. </p>
</dd>
</dl>

## -returns
<p><b>ExInterlockedAddUlong </b>returns the original (unsummed) value of the <i>Addend</i>. </p>

## -remarks
<p>Consider using <b>InterlockedExchangeAdd</b> instead of this routine. <b>InterlockedExchangeAdd</b> can be more efficient because it does not use a spin lock and it is inlined by the compiler.</p>

<p>Support routines that do interlocked operations are assumed to be incapable of causing a page fault. That is, neither their code nor any of the data they touch can cause a page fault without bringing down the system. They use spin locks to achieve atomicity on symmetric multiprocessor machines. The caller must provide resident storage for the <i>Lock</i>, which must be initialized with <b>KeInitializeSpinLock</b> before the initial call to an <b>ExInterlocked<i>Xxx</i></b>.</p>

<p>The <i>Lock</i> passed to <b>ExInterlockedAddULong</b> is used to assure that the add operation on <i>Addend</i> is atomic with respect to any other operations on the same value which synchronize with this same spin lock. </p>

<p><b>ExInterlockedAddUlong</b> masks interrupts. Consequently, it can be used for synchronization between an ISR and other driver code, provided that the same <i>Lock</i> is never reused in a call to a routine that runs at IRQL = DISPATCH_LEVEL.</p>

<p>Note that calls to <b>Interlocked<i>Xxx</i></b> are guaranteed to be atomic with respect to other <b>Interlocked<i>Xxx</i></b> calls without caller-supplied spin locks.</p>

<p>Callers of <b>ExInterlockedAddUlong</b> run at any IRQL. The storage for the <i>Addend</i> parameter must be resident at all IRQLs.</p>

<p>Consider using <b>InterlockedExchangeAdd</b> instead of this routine. <b>InterlockedExchangeAdd</b> can be more efficient because it does not use a spin lock and it is inlined by the compiler.</p>

<p>Support routines that do interlocked operations are assumed to be incapable of causing a page fault. That is, neither their code nor any of the data they touch can cause a page fault without bringing down the system. They use spin locks to achieve atomicity on symmetric multiprocessor machines. The caller must provide resident storage for the <i>Lock</i>, which must be initialized with <b>KeInitializeSpinLock</b> before the initial call to an <b>ExInterlocked<i>Xxx</i></b>.</p>

<p>The <i>Lock</i> passed to <b>ExInterlockedAddULong</b> is used to assure that the add operation on <i>Addend</i> is atomic with respect to any other operations on the same value which synchronize with this same spin lock. </p>

<p><b>ExInterlockedAddUlong</b> masks interrupts. Consequently, it can be used for synchronization between an ISR and other driver code, provided that the same <i>Lock</i> is never reused in a call to a routine that runs at IRQL = DISPATCH_LEVEL.</p>

<p>Note that calls to <b>Interlocked<i>Xxx</i></b> are guaranteed to be atomic with respect to other <b>Interlocked<i>Xxx</i></b> calls without caller-supplied spin locks.</p>

<p>Callers of <b>ExInterlockedAddUlong</b> run at any IRQL. The storage for the <i>Addend</i> parameter must be resident at all IRQLs.</p>

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
<p>Any level (see Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545335">ExInterlockedAddLargeInteger</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547910">InterlockedIncrement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547871">InterlockedDecrement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ExInterlockedAddUlong routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
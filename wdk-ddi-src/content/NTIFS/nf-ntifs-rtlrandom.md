---
UID: NF.ntifs.RtlRandom
title: RtlRandom
author: windows-driver-content
description: The RtlRandom routine returns a random number that was generated from a given seed value.
old-location: ifsk\rtlrandom.htm
ms.assetid: f3975ad7-8eb8-4f46-8024-6a1decc21c77
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h, Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows 2000 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlRandom
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
req.irql: < DISPATCH_LEVEL
ms.keywords: RtlRandom
req.iface: 
---

# RtlRandom function



## -description
<p>The <b>RtlRandom</b> routine returns a random number that was generated from a given seed value. </p>


## -syntax

````
ULONG RtlRandom(
  _Inout_ PULONG Seed
);
````


## -parameters
<dl>

### -param <i>Seed</i> [in, out]

<dd>
<p>Unsigned long value from which to generate a random number. </p>
</dd>
</dl>

## -returns
<p><b>RtlRandom</b> returns a random number in the range [0..MAXLONG-1]. </p>

## -remarks
<p><b>RtlRandom</b> returns values that are uniformly distributed over the range from zero to the maximum possible LONG value less 1 if it is called repeatedly with the same <i>Seed</i>.</p>

<p>The <b>RtlRandomEx</b> function is an improved version of the <b>RtlRandom</b> function that is twice as fast and produces better random numbers. </p>

<p><b>RtlRandom</b> returns values that are uniformly distributed over the range from zero to the maximum possible LONG value less 1 if it is called repeatedly with the same <i>Seed</i>.</p>

<p>The <b>RtlRandomEx</b> function is an improved version of the <b>RtlRandom</b> function that is twice as fast and produces better random numbers. </p>

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
<p>Available in Microsoft Windows 2000 and later.</p>
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
<p>&lt; DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553181">RtlRandomEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlRandom routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
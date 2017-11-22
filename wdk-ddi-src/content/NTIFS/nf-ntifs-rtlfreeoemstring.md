---
UID: NF.ntifs.RtlFreeOemString
title: RtlFreeOemString
author: windows-driver-content
description: The RtlFreeOemString routine releases storage that was allocated by any of the Rtl..ToOemString routines.
old-location: ifsk\rtlfreeoemstring.htm
ms.assetid: cd9bc03d-1f57-420c-9430-d2d742f654e1
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
req.alt-api: RtlFreeOemString
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
ms.keywords: RtlFreeOemString
req.iface: 
---

# RtlFreeOemString function



## -description
<p>The <b>RtlFreeOemString</b> routine releases storage that was allocated by any of the <b>Rtl..ToOemString</b> routines. </p>


## -syntax

````
VOID RtlFreeOemString(
  _Inout_ POEM_STRING OemString
);
````


## -parameters
<dl>

### -param <i>OemString</i> [in, out]

<dd>
<p>Pointer to the OEM string buffer that was allocated by a preceding call to <b>RtlUnicodeStringToCountedOemString</b>, <b>RtlUnicodeStringToOemString</b>, <b>RtlUpcaseUnicodeStringToCountedOemString</b>, or <b>RtlUpcaseUnicodeStringToOemString</b>. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>RtlFreeOemString</b> deallocates memory only for the buffered OEM string. This routine does not free the buffered Unicode string passed in a preceding call to the <b>Rtl..ToOemString</b> routine. </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

<p><b>RtlFreeOemString</b> deallocates memory only for the buffered OEM string. This routine does not free the buffered Unicode string passed in a preceding call to the <b>Rtl..ToOemString</b> routine. </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

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
<p>&lt; DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558741">OEM_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553251">RtlUnicodeStringToCountedOemString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553255">RtlUnicodeStringToOemString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553277">RtlUpcaseUnicodeStringToCountedOemString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553282">RtlUpcaseUnicodeStringToOemString</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlFreeOemString routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
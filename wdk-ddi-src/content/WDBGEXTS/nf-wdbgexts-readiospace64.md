---
UID: NF.wdbgexts.ReadIoSpace64
title: ReadIoSpace64
author: windows-driver-content
description: The ReadIoSpace64 function reads from the system I/O locations.
old-location: debugger\readiospace64.htm
ms.assetid: 7578df0d-67ea-4a8c-a89c-6a9d95bff33a
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: wdbgexts.h
req.include-header: Wdbgexts.h, Wdbgexts.h, Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ReadIoSpace64
req.alt-loc: wdbgexts.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: ReadIoSpace64
req.iface: 
req.product: Windows 10 or later.
---

# ReadIoSpace64 function



## -description
<p>The <b>ReadIoSpace64</b> function reads from the system I/O locations. </p>


## -syntax

````
__inline VOID ReadIoSpace64(
   ULONG64 address,
   PULONG  data,
   PULONG  size
);
````


## -parameters
<dl>

### -param <i>address</i> 

<dd>
<p>Specifies the I/O address to read from.</p>
</dd>

### -param <i>data</i> 

<dd>
<p>Specifies the address of a variable to hold the data read. This must be at least the number of bytes contained in <i>size</i>.</p>
</dd>

### -param <i>size</i> 

<dd>
<p>Specifies the address of a variable that contains the number of bytes to read. <i>Size</i> must be 1, 2, or 4. After the data is read, <i>size</i> will contain the number of bytes actually read.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>If you are writing 32-bit code, you should use <a href="https://msdn.microsoft.com/library/windows/hardware/ff553574">ReadIoSpace</a> instead. See <a href="https://msdn.microsoft.com/library/windows/hardware/ff537780">32-Bit Pointers and 64-Bit Pointers</a> for details.</p>

<p>If you are writing a WdbgExts extension, include <b>wdbgexts.h</b>. If you are writing a DbgEng extension that calls this function, include <b>wdbgexts.h</b> before <b>dbgeng.h</b> (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff561480">Writing DbgEng Extension Code</a> for details).
</p>

<p>If you are writing 32-bit code, you should use <a href="https://msdn.microsoft.com/library/windows/hardware/ff553574">ReadIoSpace</a> instead. See <a href="https://msdn.microsoft.com/library/windows/hardware/ff537780">32-Bit Pointers and 64-Bit Pointers</a> for details.</p>

<p>If you are writing a WdbgExts extension, include <b>wdbgexts.h</b>. If you are writing a DbgEng extension that calls this function, include <b>wdbgexts.h</b> before <b>dbgeng.h</b> (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff561480">Writing DbgEng Extension Code</a> for details).
</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdbgexts.h (include Wdbgexts.h, Wdbgexts.h, or Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>
---
UID: NF.wdbgexts.ReadMsr
title: ReadMsr
author: windows-driver-content
description: The ReadMsr function reads the contents of a Model-Specific Register (MSR).
old-location: debugger\readmsr.htm
ms.assetid: 1cb51f88-a943-43e6-af18-0e9e301d8382
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
req.alt-api: ReadMsr
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
ms.keywords: ReadMsr
req.iface: 
req.product: Windows 10 or later.
---

# ReadMsr function



## -description
<p>The <b>ReadMsr</b> function reads the contents of a Model-Specific Register (MSR). </p>


## -syntax

````
__inline VOID ReadMsr(
   ULONG     MsrReg,
   ULONGLONG *MsrValue
);
````


## -parameters
<dl>

### -param <i>MsrReg</i> 

<dd>
<p>Specifies the ID number of the MSR.</p>
</dd>

### -param <i>MsrValue</i> 

<dd>
<p>Receives the value of the MSR.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>If you are writing a WdbgExts extension, include <b>wdbgexts.h</b>. If you are writing a DbgEng extension that calls this function, include <b>wdbgexts.h</b> before <b>dbgeng.h</b> (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff561480">Writing DbgEng Extension Code</a> for details).
</p>

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
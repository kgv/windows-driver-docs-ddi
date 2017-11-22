---
UID: NF.dbgeng.IDebugDataSpaces4.ReadControl
title: IDebugDataSpaces4::ReadControl
author: windows-driver-content
description: The ReadControl method reads implementation-specific system data.
old-location: debugger\readcontrol.htm
ms.assetid: 52f65e2a-97a7-4c1c-a021-208bc2520b7d
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugDataSpaces.ReadControl,IDebugDataSpaces2.ReadControl,IDebugDataSpaces3.ReadControl,IDebugDataSpaces4.ReadControl
req.alt-loc: dbgeng.h
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
ms.keywords: IDebugDataSpaces4, ReadControl, IDebugDataSpaces4::ReadControl
req.iface: IDebugDataSpaces4
---

# IDebugDataSpaces4::ReadControl method



## -description
<p>The <b>ReadControl</b> method reads implementation-specific system data.</p>


## -syntax

````
HRESULT ReadControl(
  [in]            ULONG   Processor,
  [in]            ULONG64 Offset,
  [out]           PVOID   Buffer,
  [in]            ULONG   BufferSize,
  [out, optional] PULONG  BytesRead
);
````


## -parameters
<dl>

### -param <i>Processor</i> [in]

<dd>
<p>Specifies the processor whose information is to be read.</p>
</dd>

### -param <i>Offset</i> [in]

<dd>
<p>Specifies the offset in the control space of the memory to read.</p>
</dd>

### -param <i>Buffer</i> [out]

<dd>
<p>Receives the data read from the control-space memory.</p>
</dd>

### -param <i>BufferSize</i> [in]

<dd>
<p>Specifies the size in bytes of the buffer <i>Buffer</i>.  This is the maximum number of bytes that will be read.</p>
</dd>

### -param <i>BytesRead</i> [out, optional]

<dd>
<p>Receives the number of bytes returned in the buffer <i>Buffer</i>.  If <i>BytesRead</i> is <b>NULL</b>, this information is not returned.</p>
</dd>
</dl>

## -returns
<dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

<p>This method can also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p>

## -remarks
<p>This method is only available in kernel-mode debugging.</p>

<p>This method is only available in kernel-mode debugging.</p>

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
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>
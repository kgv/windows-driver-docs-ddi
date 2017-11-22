---
UID: NF.dbgeng.IDebugBreakpoint2.GetOffset
title: IDebugBreakpoint2::GetOffset
author: windows-driver-content
description: The GetOffset method returns the location that triggers a breakpoint.
old-location: debugger\getoffset.htm
ms.assetid: 7da401c9-10c1-4a2b-91ea-c0f9f58fd87a
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
req.alt-api: IDebugBreakpoint.GetOffset,IDebugBreakpoint2.GetOffset
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
ms.keywords: IDebugBreakpoint2, GetOffset, IDebugBreakpoint2::GetOffset
req.iface: IDebugBreakpoint2
---

# IDebugBreakpoint2::GetOffset method



## -description
<p>The <b>GetOffset</b> method returns the location that triggers a breakpoint.</p>


## -syntax

````
HRESULT GetOffset(
  [out] PULONG64 Offset
);
````


## -parameters
<dl>

### -param <i>Offset</i> [out]

<dd>
<p>The location on the target that triggers the breakpoint.</p>
</dd>
</dl>

## -returns
<dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>E_NOINTERFACE</b></dt>
</dl><p>The breakpoint is deferred and does not currently specify a location in the target's memory address space. To determine the breakpoint location in this case, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548048">GetOffsetExpression</a>.</p>

<p> </p>

<p>This method can also return other error values.  For more information, see <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a>.</p>

## -remarks
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/ff548095">GetParameters</a> method also returns the location that triggers a breakpoint.</p>

<p>For more information about how to use breakpoints, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff560075">Using Breakpoints</a>.</p>

<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/ff548095">GetParameters</a> method also returns the location that triggers a breakpoint.</p>

<p>For more information about how to use breakpoints, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff560075">Using Breakpoints</a>.</p>

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
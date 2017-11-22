---
UID: NF.dbgeng.IDebugSymbols3.GetScope
title: IDebugSymbols3::GetScope
author: windows-driver-content
description: The GetScope method returns information about the current scope.
old-location: debugger\getscope.htm
ms.assetid: 59eb490e-66d5-4108-8d00-5503fa56665d
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h, Ntddk.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugSymbols.GetScope,IDebugSymbols2.GetScope,IDebugSymbols3.GetScope
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
ms.keywords: IDebugSymbols3, GetScope, IDebugSymbols3::GetScope
req.iface: IDebugSymbols3
---

# IDebugSymbols3::GetScope method



## -description
<p>The <b>GetScope</b> method returns information about the current scope.</p>


## -syntax

````
HRESULT GetScope(
  [out, optional] PULONG64           InstructionOffset,
  [out, optional] PDEBUG_STACK_FRAME ScopeFrame,
  [out, optional] PVOID              ScopeContext,
  [in]            ULONG              ScopeContextSize
);
````


## -parameters
<dl>

### -param <i>InstructionOffset</i> [out, optional]

<dd>
<p>Receives the location in the process's virtual address space of the current scope's current instruction.</p>
</dd>

### -param <i>ScopeFrame</i> [out, optional]

<dd>
<p>Receives the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541643">DEBUG_STACK_FRAME</a> structure representing the current scope's stack frame.</p>
</dd>

### -param <i>ScopeContext</i> [out, optional]

<dd>
<p>Receives the current scope's <a href="debugger.scopes_and_symbol_groups#thread_context#thread_context">thread context</a>.  The type of the thread context is the CONTEXT structure for the target's effective processor.  The buffer <i>ScopeContext</i> must be large enough to hold this structure.</p>
</dd>

### -param <i>ScopeContextSize</i> [in]

<dd>
<p>Specifies the size of the buffer <i>ScopeContext</i>.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>E_INVALIDARG</b></dt>
</dl><p>The size of the buffer <i>ScopeContext</i> was not large enough to hold the scope's context.</p>

<p> </p>

## -remarks
<p>For more information about scopes, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554702">Scopes and Symbol Groups</a>.</p>

<p>For more information about scopes, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554702">Scopes and Symbol Groups</a>.</p>

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
<dt>Dbgeng.h (include Dbgeng.h or Ntddk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550856">IDebugSymbols</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550864">IDebugSymbols2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550870">IDebugSymbols3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/66a5aa3d-fe35-4c30-951f-f25de75dacb0">IDebugControl::GetEffectiveProcessorType</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554577">ResetScope</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556773">SetScope</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugSymbols::GetScope method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
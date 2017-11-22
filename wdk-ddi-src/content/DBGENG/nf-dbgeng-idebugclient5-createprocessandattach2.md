---
UID: NF.dbgeng.IDebugClient5.CreateProcessAndAttach2
title: IDebugClient5::CreateProcessAndAttach2
author: windows-driver-content
description: The CreateProcessAndAttach2 method creates a process from a specified command line, then attaches to that process or another user-mode process.
old-location: debugger\createprocessandattach2.htm
ms.assetid: 2e479563-8ffd-40cd-a584-d34de2530e1d
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
req.alt-api: IDebugClient5.CreateProcessAndAttach2
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
ms.keywords: IDebugClient5, CreateProcessAndAttach2, IDebugClient5::CreateProcessAndAttach2
req.iface: IDebugClient5
---

# IDebugClient5::CreateProcessAndAttach2 method



## -description
<p>The <b>CreateProcessAndAttach2</b>  method creates a process from a specified command line, then attaches to that process or another user-mode process.</p>


## -syntax

````
HRESULT CreateProcessAndAttach2(
  [in]           ULONG64 Server,
  [in, optional] PSTR    CommandLine,
  [in]           PVOID   OptionsBuffer,
  [in]           ULONG   OptionsBufferSize,
  [in, optional] PCSTR   InitialDirectory,
  [in, optional] PCSTR   Environment,
  [in]           ULONG   ProcessId,
  [in]           ULONG   AttachFlags
);
````


## -parameters
<dl>

### -param <i>Server</i> [in]

<dd>
<p>Specifies the process server to use to attach to the process.  If <i>Server</i> is zero, the engine will connect to the local process without using a process server.</p>
</dd>

### -param <i>CommandLine</i> [in, optional]

<dd>
<p>Specifies the command line to execute to create the new process.  If <i>CommandLine</i> is <b>NULL</b>, no process is created and these methods will use <i>ProcessId</i> to attach to an existing process.</p>
</dd>

### -param <i>OptionsBuffer</i> [in]

<dd>
<p>Specifies the process creation options.  <i>OptionsBuffer</i> is a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541464">DEBUG_CREATE_PROCESS_OPTIONS</a> structure.</p>
</dd>

### -param <i>OptionsBufferSize</i> [in]

<dd>
<p>Specifies the size of the buffer <i>OptionsBuffer</i>.  This should be set to <b>sizeof(DEBUG_CREATE_PROCESS_OPTIONS)</b>.</p>
</dd>

### -param <i>InitialDirectory</i> [in, optional]

<dd>
<p>Specifies the starting directory for the process.  This parameter is used only if <i>CommandLine</i> is not <b>NULL</b>.  If <i>InitialDirectory</i> is <b>NULL</b>, the current directory for the process server is used.</p>
</dd>

### -param <i>Environment</i> [in, optional]

<dd>
<p>Specifies an environment block for the new process.  An environment block consists of a null-terminated block of null-terminated strings.  Each string is of the form:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>name=value</pre>
</td>
</tr>
</table></span></div>
<p>Note that the last two characters of the environment block are both <b>NULL</b>: one to terminate the string and one to terminate the block.</p>
<p>If <i>Environment</i> is set to <b>NULL</b>, the new process inherits the environment block of the process server.  If the DEBUG_CREATE_PROCESS_THROUGH_RTL flag is set in <i>OptionsBuffer</i>, then <i>Environment</i> must be <b>NULL</b>.</p>
</dd>

### -param <i>ProcessId</i> [in]

<dd>
<p>Specifies the process ID of the target process to which the debugger will attach.  If <i>ProcessID</i> is zero, the debugger will attach to the process it created from <i>CommandLine</i>.</p>
</dd>

### -param <i>AttachFlags</i> [in]

<dd>
<p>Specifies the flags that control how the debugger attaches to the target process.  For details on these flags, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541454">DEBUG_ATTACH_XXX</a>.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>E_INVALIDARG</b></dt>
</dl><p>This is returned if <i>CommandLine</i> is <b>NULL</b> and <i>ProcessId</i> is zero.</p>

<p> </p>

## -remarks
<p>This method is available only for live user-mode debugging.</p>

<p>If <i>CommandLine</i> is not <b>NULL</b> and <i>ProcessId</i> is not zero, then the engine will create the process in a suspended state.  The engine will resume this newly created process after it successfully connects to the process specified in <i>ProcessId</i>.</p>

<p>For more information about creating and attaching to live user-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552020">Live User-Mode Targets</a>.</p>

<p>This method is available only for live user-mode debugging.</p>

<p>If <i>CommandLine</i> is not <b>NULL</b> and <i>ProcessId</i> is not zero, then the engine will create the process in a suspended state.  The engine will resume this newly created process after it successfully connects to the process specified in <i>ProcessId</i>.</p>

<p>For more information about creating and attaching to live user-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552020">Live User-Mode Targets</a>.</p>

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

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550497">IDebugClient5</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538150">AttachProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562135">.attach (Attach to Process)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562280">.create (Create Process)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539237">ConnectProcessServer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539323">CreateProcess2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548265">GetRunningProcessSystemIds</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548243">GetRunningProcessDescription</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541846">DetachCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558866">TerminateCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537786">AbandonCurrentProcess</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugClient5::CreateProcessAndAttach2 method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
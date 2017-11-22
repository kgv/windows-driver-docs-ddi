---
UID: NF.wdm.DbgBreakPoint
title: DbgBreakPoint
author: windows-driver-content
description: The DbgBreakPoint routine breaks into the kernel debugger.
old-location: devtest\dbgbreakpoint.htm
ms.assetid: deeac910-2cc3-4a54-bf3b-aeb56d0004dc
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: devtest
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DbgBreakPoint
req.alt-loc: NtDll.dll,NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtDll.lib (user mode); 
NtosKrnl.lib (kernel mode)
req.dll: NtDll.dll (user mode); 
NtosKrnl.exe (kernel mode)
req.irql: 
ms.keywords: DbgBreakPoint
req.iface: 
req.product: Windows 10 or later.
---

# DbgBreakPoint function



## -description
<p>The <b>DbgBreakPoint</b> routine breaks into the kernel debugger.</p>


## -syntax

````
VOID DbgBreakPoint(void);
````


## -parameters


## -returns
<p>None</p>

<p>None</p>

<p>None</p>

## -remarks
<p>The <b>DbgBreakPoint</b> routine is the kernel-mode equivalent of <b>DebugBreak</b>.</p>

<p>This routine raises an exception that is handled by the kernel debugger if one is installed; otherwise, it is handled by the debug system. If a debugger is not connected to the system, the exception can be handled in the standard way.</p>

<p>In kernel mode, a break exception that is not handled will cause a bug check. You can, however, connect a kernel-mode debugger to a target computer that has stopped responding and has kernel debugging enabled. For more information, see <a href="https://msdn.microsoft.com/938ef180-84de-442f-9b6c-1138c2fc8d5a">Windows Debugging</a>.</p>

<p>The <b>DbgBreakPoint</b> routine is the kernel-mode equivalent of <b>DebugBreak</b>.</p>

<p>This routine raises an exception that is handled by the kernel debugger if one is installed; otherwise, it is handled by the debug system. If a debugger is not connected to the system, the exception can be handled in the standard way.</p>

<p>In kernel mode, a break exception that is not handled will cause a bug check. You can, however, connect a kernel-mode debugger to a target computer that has stopped responding and has kernel debugging enabled. For more information, see <a href="https://msdn.microsoft.com/938ef180-84de-442f-9b6c-1138c2fc8d5a">Windows Debugging</a>.</p>

<p>The <b>DbgBreakPoint</b> routine is the kernel-mode equivalent of <b>DebugBreak</b>.</p>

<p>This routine raises an exception that is handled by the kernel debugger if one is installed; otherwise, it is handled by the debug system. If a debugger is not connected to the system, the exception can be handled in the standard way.</p>

<p>In kernel mode, a break exception that is not handled will cause a bug check. You can, however, connect a kernel-mode debugger to a target computer that has stopped responding and has kernel debugging enabled. For more information, see <a href="https://msdn.microsoft.com/938ef180-84de-442f-9b6c-1138c2fc8d5a">Windows Debugging</a>.</p>

<p>The <b>DbgBreakPoint</b> routine is the kernel-mode equivalent of <b>DebugBreak</b>.</p>

<p>This routine raises an exception that is handled by the kernel debugger if one is installed; otherwise, it is handled by the debug system. If a debugger is not connected to the system, the exception can be handled in the standard way.</p>

<p>In kernel mode, a break exception that is not handled will cause a bug check. You can, however, connect a kernel-mode debugger to a target computer that has stopped responding and has kernel debugging enabled. For more information, see <a href="https://msdn.microsoft.com/938ef180-84de-442f-9b6c-1138c2fc8d5a">Windows Debugging</a>.</p>

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
<dt>Ntddk.h (include Wdm.h or Ntddk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtDll.lib (user mode); </dt>
<dt>NtosKrnl.lib (kernel mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtDll.dll (user mode); </dt>
<dt>NtosKrnl.exe (kernel mode)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543629">DbgBreakPointWithStatus</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548063">KdBreakPoint</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548065">KdBreakPointWithStatus</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [devtest\devtest]:%20DbgBreakPoint routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
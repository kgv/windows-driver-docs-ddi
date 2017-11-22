---
UID: NF.fltkernel.FltGetRoutineAddress
title: FltGetRoutineAddress
author: windows-driver-content
description: The FltGetRoutineAddress routine returns a pointer to a routine specified by the FltMgrRoutineName parameter.
old-location: ifsk\fltgetroutineaddress.htm
ms.assetid: b2b74e79-5840-41a0-8af3-3d13e209aea7
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltGetRoutineAddress
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: <= DISPATCH_LEVEL
ms.keywords: FltGetRoutineAddress
req.iface: 
---

# FltGetRoutineAddress function



## -description
<p>The <b>FltGetRoutineAddress</b> routine returns a pointer to a routine specified by the <i>FltMgrRoutineName</i> parameter. </p>


## -syntax

````
PVOID FltGetRoutineAddress(
  _In_ PCSTR FltMgrRoutineName
);
````


## -parameters
<dl>

### -param <i>FltMgrRoutineName</i> [in]

<dd>
<p>Name of the filter manager routine to resolve. </p>
</dd>
</dl>

## -returns
<p>If the routine name can be resolved, <b>FltGetRoutineAddress</b> returns a pointer to the routine. Otherwise, it returns <b>NULL</b>. </p>

## -remarks
<p><b>FltGetRoutineAddress</b> searches the filter manager's export table for the requested routine name. </p>

<p>To get the addresses of other routines that are exported by the kernel or hardware abstraction layer (HAL), use <a href="https://msdn.microsoft.com/library/windows/hardware/ff554563">MmGetSystemRoutineAddress</a>. </p>

<p>Note that in Windows 2000 and Windows XP, before FltGetRoutineAddress is called at least one minifilter on the system must call FltRegisterFilter. The call to FltRegisterFilter is necessary to initialize global data structures.</p>

<p><b>FltGetRoutineAddress</b> searches the filter manager's export table for the requested routine name. </p>

<p>To get the addresses of other routines that are exported by the kernel or hardware abstraction layer (HAL), use <a href="https://msdn.microsoft.com/library/windows/hardware/ff554563">MmGetSystemRoutineAddress</a>. </p>

<p>Note that in Windows 2000 and Windows XP, before FltGetRoutineAddress is called at least one minifilter on the system must call FltRegisterFilter. The call to FltRegisterFilter is necessary to initialize global data structures.</p>

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
<dt>Fltkernel.h (include Fltkernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>FltMgr.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Fltmgr.sys</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554563">MmGetSystemRoutineAddress</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltGetRoutineAddress routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
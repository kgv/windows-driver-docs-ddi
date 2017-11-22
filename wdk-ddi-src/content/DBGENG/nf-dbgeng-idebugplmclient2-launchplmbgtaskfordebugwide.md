---
UID: NF.dbgeng.IDebugPlmClient2.LaunchPlmBgTaskForDebugWide
title: IDebugPlmClient2::LaunchPlmBgTaskForDebugWide
author: windows-driver-content
description: Launches a suspended Process Lifecycle Management (PLM) background task.
old-location: debugger\idebugplmclient2_launchplmbgtaskfordebugwide.htm
ms.assetid: 47793815-F7AC-4E0D-809C-DBB7497BDA30
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugPlmClient2.LaunchPlmBgTaskForDebugWide
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
ms.keywords: IDebugPlmClient2, LaunchPlmBgTaskForDebugWide, IDebugPlmClient2::LaunchPlmBgTaskForDebugWide
req.iface: IDebugPlmClient2
---

# IDebugPlmClient2::LaunchPlmBgTaskForDebugWide method



## -description
<p>Launches a suspended Process Lifecycle Management (PLM) background task.</p>


## -syntax

````
HRESULT LaunchPlmBgTaskForDebugWide(
  [in]  ULONG64 Server,
  [in]  ULONG   Timeout,
  [in]  PCWSTR  PackageFullName,
  [in]  PCWSTR  BackgroundTaskId,
  [out] PULONG  ProcessId,
  [out] PULONG  ThreadId
);
````


## -parameters
<dl>

### -param <i>Server</i> [in]

<dd>
<p>The server of the task.</p>
</dd>

### -param <i>Timeout</i> [in]

<dd>
<p>A time-out value.</p>
</dd>

### -param <i>PackageFullName</i> [in]

<dd>
<p>A pointer to the package name.</p>
</dd>

### -param <i>BackgroundTaskId</i> [in]

<dd>
<p>A pointer to the task ID.</p>
</dd>

### -param <i>ProcessId</i> [out]

<dd>
<p>A pointer to a process ID output.</p>
</dd>

### -param <i>ThreadId</i> [out]

<dd>
<p>A pointer to a thread ID output.</p>
</dd>
</dl>

## -returns
<p>If this method succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.</p>

## -remarks


## -requirements
<table>
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
<a href="https://msdn.microsoft.com/22AACAD1-292B-42D9-95F7-A3654E2077FB">IDebugPlmClient2</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugPlmClient2::LaunchPlmBgTaskForDebugWide method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
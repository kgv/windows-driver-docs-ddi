---
UID: NF.ntifs.IoGetRequestorSessionId
title: IoGetRequestorSessionId
author: windows-driver-content
description: The IoGetRequestorSessionId routine returns the session ID for the process that originally requested a given I/O operation.
old-location: ifsk\iogetrequestorsessionid.htm
ms.assetid: 9e13cf62-d71e-4878-becd-d34beb2f59b3
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Microsoft Windows Server 2003 SP1 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoGetRequestorSessionId
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
req.irql: <= APC_LEVEL
ms.keywords: IoGetRequestorSessionId
req.iface: 
---

# IoGetRequestorSessionId function



## -description
<p>The <b>IoGetRequestorSessionId</b> routine returns the session ID for the process that originally requested a given I/O operation.</p>


## -syntax

````
NTSTATUS IoGetRequestorSessionId(
  _In_  PIRP   Irp,
  _Out_ PULONG pSessionId
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in]

<dd>
<p>A pointer to the I/O request packet (IRP) for the I/O operation. </p>
</dd>

### -param <i>pSessionId</i> [out]

<dd>
<p>A pointer to a caller-allocated variable that receives the session ID for the process that requested the I/O operation. If the call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff548391">IoGetRequestorProcessId</a> fails, this variable is set to -1.</p>
</dd>
</dl>

## -returns
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548391">IoGetRequestorProcessId</a> returns STATUS_SUCCESS if the session ID is successfully returned, STATUS_UNSUCCESSFUL otherwise. STATUS_UNSUCCESSFUL is an error NTSTATUS value. </p>

## -remarks


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
<p>Version</p>
</th>
<td width="70%">
<p>This routine is available on Microsoft Windows Server 2003 SP1 and later. </p>
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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548385">IoGetRequestorProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548391">IoGetRequestorProcessId</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20IoGetRequestorSessionId routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
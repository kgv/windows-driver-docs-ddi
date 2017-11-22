---
UID: NF.wdm.PoGetSystemWake
title: PoGetSystemWake
author: windows-driver-content
description: The PoGetSystemWake routine determines whether a specified IRP has been marked as waking the system from a sleeping state.
old-location: kernel\pogetsystemwake.htm
ms.assetid: f2e6bcd6-ed6b-4c88-af96-768284bddb24
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PoGetSystemWake
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
req.irql: <=DISPATCH_LEVEL
ms.keywords: PoGetSystemWake
req.iface: 
req.product: Windows 10 or later.
---

# PoGetSystemWake function



## -description
<p>The <b>PoGetSystemWake</b> routine determines whether a specified IRP has been marked as waking the system from a sleeping state.</p>


## -syntax

````
BOOLEAN PoGetSystemWake(
  _In_ PIRP Irp
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in]

<dd>
<p>A pointer to an IRP.</p>
</dd>
</dl>

## -returns
<p><b>PoGetSystemWake</b> returns one of the following:</p><dl>
<dt><b><b>TRUE</b></b></dt>
</dl><p>The specified IRP did cause the system to wake.</p><dl>
<dt><b><b>FALSE</b></b></dt>
</dl><p>The specified IRP did not cause the system to wake.</p>

<p> </p>

## -remarks
<p>A driver calls <b>PoGetSystemWake</b> to determine if a specified IRP contributed to waking the system from a sleep state.</p>

<p>A driver in a wait/wake chain should call <b>PoGetSystemWake</b> on its own wait/wake IRP at completion to determine if the driver should also call <a href="https://msdn.microsoft.com/library/windows/hardware/ff559770">PoSetSystemWake</a> for child wait/wake IRPs that the driver is about to complete. This ensures that system wake information properly propagates throughout the entire wait/wake chain.</p>

<p>It is possible that several IRPs are causing the system to wake. In this case, <b>PoGetSystemWake </b>would return <b>TRUE</b> for all of the IRPs contributing to the wake event.</p>

<p>A driver calls <b>PoGetSystemWake</b> to determine if a specified IRP contributed to waking the system from a sleep state.</p>

<p>A driver in a wait/wake chain should call <b>PoGetSystemWake</b> on its own wait/wake IRP at completion to determine if the driver should also call <a href="https://msdn.microsoft.com/library/windows/hardware/ff559770">PoSetSystemWake</a> for child wait/wake IRPs that the driver is about to complete. This ensures that system wake information properly propagates throughout the entire wait/wake chain.</p>

<p>It is possible that several IRPs are causing the system to wake. In this case, <b>PoGetSystemWake </b>would return <b>TRUE</b> for all of the IRPs contributing to the wake event.</p>

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
<p>Available starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559770">PoSetSystemWake</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PoGetSystemWake routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.ntddk.PshedFreeMemory
title: PshedFreeMemory
author: windows-driver-content
description: The PshedFreeMemory function frees a block of memory that was previously allocated by calling the PshedAllocateMemory function.
old-location: whea\pshedfreememory.htm
ms.assetid: e0784b46-9929-480c-88d0-9983d80fd753
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: whea
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PshedFreeMemory
req.alt-loc: Pshed.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Pshed.lib
req.dll: Pshed.dll
req.irql: <=DISPATCH_LEVEL
ms.keywords: PshedFreeMemory
req.iface: 
---

# PshedFreeMemory function



## -description
<p>The <b>PshedFreeMemory</b> function frees a block of memory that was previously allocated by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559461">PshedAllocateMemory</a> function.</p>


## -syntax

````
VOID PshedFreeMemory(
  _In_ PVOID Address
);
````


## -parameters
<dl>

### -param <i>Address</i> [in]

<dd>
<p>A pointer to the block of memory being freed.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A PSHED plug-in calls the <b>PshedFreeMemory</b> function to free a block of memory that it previously allocated by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559461">PshedAllocateMemory</a> function.</p>

<p>A PSHED plug-in calls the <b>PshedFreeMemory</b> function to free a block of memory that it previously allocated by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559461">PshedAllocateMemory</a> function.</p>

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
<p>Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Pshed.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Pshed.dll</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559461">PshedAllocateMemory</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [whea\whea]:%20PshedFreeMemory function%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
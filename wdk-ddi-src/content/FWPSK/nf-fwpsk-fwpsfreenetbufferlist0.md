---
UID: NF.fwpsk.FwpsFreeNetBufferList0
title: FwpsFreeNetBufferList0
author: windows-driver-content
description: The FwpsFreeNetBufferList0 function frees a NET_BUFFER_LIST structure that was previously allocated by a call to the FwpsAllocateNetBufferAndNetBufferList0 function.Note  FwpsFreeNetBufferList0 is a specific version of FwpsFreeNetBufferList.
old-location: netvista\fwpsfreenetbufferlist0.htm
ms.assetid: 7e337d7a-a408-4574-8da3-ea333fdbde8b
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FwpsFreeNetBufferList0
req.alt-loc: fwpkclnt.lib,fwpkclnt.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fwpkclnt.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: FwpsFreeNetBufferList0
req.iface: 
---

# FwpsFreeNetBufferList0 function



## -description
<p>The 
  <b>FwpsFreeNetBufferList0</b> function frees a 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure that was previously
  allocated by a call to the 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff551135">FwpsAllocateNetBufferAndNetBufferList0</a> function.</p>


## -syntax

````
void NTAPI FwpsFreeNetBufferList0(
  _Inout_ NET_BUFFER_LIST *netBufferList
);
````


## -parameters
<dl>

### -param <i>netBufferList</i> [in, out]

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure that is being
     freed.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A callout driver calls the 
    <b>FwpsFreeNetBufferList0</b> function to free a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure that was
    previously allocated by a call to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff551135">FwpsAllocateNetBufferAndNetBufferList0</a> function.</p>

<p>A callout driver calls the 
    <b>FwpsFreeNetBufferList0</b> function to free a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure that was
    previously allocated by a call to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff551135">FwpsAllocateNetBufferAndNetBufferList0</a> function.</p>

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
<dt>Fwpsk.h (include Fwpsk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Fwpkclnt.lib</dt>
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
<a href="https://msdn.microsoft.com/d7f2d3c0-f2c9-4624-b3e1-9fbbf64c7186">
   FwpsAllocateNetBufferAndNetBufferList0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FwpsFreeNetBufferList0 function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
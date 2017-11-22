---
UID: NF.ndis.NdisAdvanceNetBufferDataStart
title: NdisAdvanceNetBufferDataStart
author: windows-driver-content
description: Call the NdisAdvanceNetBufferDataStart function to release the used data space that was added with the NdisRetreatNetBufferDataStart function.
old-location: netvista\ndisadvancenetbufferdatastart.htm
ms.assetid: 49b69282-137d-4bb5-92f5-4d27cedbb6d4
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisAdvanceNetBufferDataStart
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_NetBuffer_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisAdvanceNetBufferDataStart
req.iface: 
---

# NdisAdvanceNetBufferDataStart function



## -description
<p>Call the 
  <b>NdisAdvanceNetBufferDataStart</b> function to release the 
  <i>used data space</i> that was added with the 
  <a href="https://msdn.microsoft.com/4b58a1dc-8a5a-464b-a2a2-deb952febe25">
  NdisRetreatNetBufferDataStart</a> function.</p>


## -syntax

````
VOID NdisAdvanceNetBufferDataStart(
  _In_     PNET_BUFFER                 NetBuffer,
  _In_     ULONG                       DataOffsetDelta,
  _In_     BOOLEAN                     FreeMdl,
  _In_opt_ NET_BUFFER_FREE_MDL_HANDLER FreeMdlHandler
);
````


## -parameters
<dl>

### -param <i>NetBuffer</i> [in]

<dd>
<p>A pointer to a previously allocated 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a> structure.</p>
</dd>

### -param <i>DataOffsetDelta</i> [in]

<dd>
<p>The amount of 
     <i>used data space</i> to release. NDIS adjusts the value of the 
     <b>DataOffset</b> member of the NET_BUFFER structure accordingly.</p>
</dd>

### -param <i>FreeMdl</i> [in]

<dd>
<p>A BOOLEAN value that, if <b>TRUE</b>, requests NDIS to free any MDLs that become unused in the advance
     operation. If 
     <i>FreeMdl</i> is <b>FALSE</b>, NDIS retains unused MDLs for use in subsequent retreat operations.</p>
</dd>

### -param <i>FreeMdlHandler</i> [in, optional]

<dd>
<p>An optional entry point for an 
     <a href="https://msdn.microsoft.com/a92b2de9-231d-4dcc-8220-857063a35eb1">NetFreeMdl</a> function. If the caller
     specifies an entry point for the 
     <i>NetFreeMdl</i> function, NDIS calls 
     <i>NetFreeMdl</i> to free an MDL and memory.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>If NDIS allocated memory to satisfy a corresponding call to the 
    <a href="https://msdn.microsoft.com/4b58a1dc-8a5a-464b-a2a2-deb952febe25">
    NdisRetreatNetBufferDataStart</a> function, then 
    <b>NdisAdvanceNetBufferDataStart</b> frees the memory that 
    <b>NdisRetreatNetBufferDataStart</b> allocated. Otherwise, the memory remains in the MDL and only the
    value of the 
    <b>DataOffset</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a> structure is modified.</p>

<p>NDIS calls the 
    <a href="https://msdn.microsoft.com/a92b2de9-231d-4dcc-8220-857063a35eb1">NetFreeMdl</a> function specified at 
    <i>FreeMdl</i> if 
    <b>NdisAdvanceNetBufferDataStart</b> must free memory. NDIS calls 
    <i>NetFreeMdl</i> only to free the MDLs and memory that the driver allocated in the 
    <a href="https://msdn.microsoft.com/14247f48-7ef8-481c-aa1e-e657475812fa">NetAllocateMdl</a> function.</p>

<p>When protocol drivers call 
    <b>NdisAdvanceNetBufferDataStart</b> on the receive path to access the various transport headers, the MDL
    chain should not be modified and 
    <i>FreeMdl</i> is <b>FALSE</b>.</p>

<p>If NDIS allocated memory to satisfy a corresponding call to the 
    <a href="https://msdn.microsoft.com/4b58a1dc-8a5a-464b-a2a2-deb952febe25">
    NdisRetreatNetBufferDataStart</a> function, then 
    <b>NdisAdvanceNetBufferDataStart</b> frees the memory that 
    <b>NdisRetreatNetBufferDataStart</b> allocated. Otherwise, the memory remains in the MDL and only the
    value of the 
    <b>DataOffset</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a> structure is modified.</p>

<p>NDIS calls the 
    <a href="https://msdn.microsoft.com/a92b2de9-231d-4dcc-8220-857063a35eb1">NetFreeMdl</a> function specified at 
    <i>FreeMdl</i> if 
    <b>NdisAdvanceNetBufferDataStart</b> must free memory. NDIS calls 
    <i>NetFreeMdl</i> only to free the MDLs and memory that the driver allocated in the 
    <a href="https://msdn.microsoft.com/14247f48-7ef8-481c-aa1e-e657475812fa">NetAllocateMdl</a> function.</p>

<p>When protocol drivers call 
    <b>NdisAdvanceNetBufferDataStart</b> on the receive path to access the various transport headers, the MDL
    chain should not be modified and 
    <i>FreeMdl</i> is <b>FALSE</b>.</p>

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
<p>Supported in NDIS 6.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547985">Irql_NetBuffer_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/14247f48-7ef8-481c-aa1e-e657475812fa">NetAllocateMdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a92b2de9-231d-4dcc-8220-857063a35eb1">NetFreeMdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/4b58a1dc-8a5a-464b-a2a2-deb952febe25">
   NdisRetreatNetBufferDataStart</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisAdvanceNetBufferDataStart function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
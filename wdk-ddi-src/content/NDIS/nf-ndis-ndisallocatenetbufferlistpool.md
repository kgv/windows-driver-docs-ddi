---
UID: NF.ndis.NdisAllocateNetBufferListPool
title: NdisAllocateNetBufferListPool
author: windows-driver-content
description: Call the NdisAllocateNetBufferListPool function to allocate a pool of NET_BUFFER_LIST structures.
old-location: netvista\ndisallocatenetbufferlistpool.htm
ms.assetid: b117b472-0c26-41a9-b364-3d0cfbd26cc9
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
req.alt-api: NdisAllocateNetBufferListPool
req.alt-loc: ndis.sys
req.ddi-compliance: Irql_NetBuffer_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: Ndis.sys
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisAllocateNetBufferListPool
req.iface: 
---

# NdisAllocateNetBufferListPool function



## -description
<p>Call the 
  <b>NdisAllocateNetBufferListPool</b> function to allocate a pool of 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures.</p>


## -syntax

````
NDIS_HANDLE NdisAllocateNetBufferListPool(
  _In_opt_ NDIS_HANDLE                      NdisHandle,
  _In_     PNET_BUFFER_LIST_POOL_PARAMETERS Parameters
);
````


## -parameters
<dl>

### -param <i>NdisHandle</i> [in, optional]

<dd>
<p>An NDIS handle that was obtained during caller initialization.</p>
</dd>

### -param <i>Parameters</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh205394">NET_BUFFER_LIST_POOL_PARAMETERS</a> structure that defines the parameters for the pool.</p>
</dd>
</dl>

## -returns
<p><b>NdisAllocateNetBufferListPool</b> returns a handle to the NET_BUFFER_LIST structure pool that NDIS
     allocates. If the allocation was unsuccessful, this handle is <b>NULL</b>. This handle is a required parameter
     in subsequent calls to NDIS functions that allocate and free NET_BUFFER_LIST structures from this
     pool.</p>

## -remarks
<p>In most cases, a caller that allocates a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure will allocate and
    queue at least one 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a> structure on that NET_BUFFER_LIST
    structure. It is more efficient to preallocate NET_BUFFER structures when you allocate a pool of
    NET_BUFFER_LIST structures than allocating NET_BUFFER_LIST structures and NET_BUFFER structures
    separately.</p>

<p>You can call the 
    <b>NdisAllocateNetBufferListPool</b> function with the 
    <b>fAllocateNetBuffer</b> value set to <b>TRUE</b> when creating a NET_BUFFER_LIST structure pool. In this case,
    a NET_BUFFER structure is preallocated with each NET_BUFFER_LIST structure that the caller allocates from
    the pool. You can call the 
    <a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
    NdisAllocateNetBufferAndNetBufferList</a> function or the 
    <a href="https://msdn.microsoft.com/9c821aac-9abd-4041-a15e-64306ada1c02">
    NdisAllocateNetBufferList</a> function to allocate NET_BUFFER_LIST structures from such a pool. Call 
    <b>NdisAllocateNetBufferAndNetBufferList</b> only if 
    <b>fAllocateNetBuffer</b> is <b>TRUE</b> and 
    <b>DataSize</b> is zero.</p>

<p>You can also call 
    <b>NdisAllocateNetBufferListPool</b> and set the 
    <b>DataSize</b> member to a nonzero value when creating a NET_BUFFER_LIST structure pool. In this case, a
    NET_BUFFER structure, MDL, and data are preallocated with each NET_BUFFER_LIST structure that the caller
    allocates from the pool.</p>

<p>NET_BUFFER structures, MDLs, and data buffers that are allocated with 
    <a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
    NdisAllocateNetBufferAndNetBufferList</a> or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561609">NdisAllocateNetBufferList</a> should
    not be freed separate from the NET_BUFFER_LIST structure. Such structures are freed with the
    NET_BUFFER_LIST structure when you call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a> function.</p>

<p>Call the 
    <a href="https://msdn.microsoft.com/811df5ea-f5e6-4986-adc0-c5fa95e5f072">
    NdisFreeNetBufferListPool</a> function to free a NET_BUFFER_LIST structure pool.</p>

<p>In most cases, a caller that allocates a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure will allocate and
    queue at least one 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a> structure on that NET_BUFFER_LIST
    structure. It is more efficient to preallocate NET_BUFFER structures when you allocate a pool of
    NET_BUFFER_LIST structures than allocating NET_BUFFER_LIST structures and NET_BUFFER structures
    separately.</p>

<p>You can call the 
    <b>NdisAllocateNetBufferListPool</b> function with the 
    <b>fAllocateNetBuffer</b> value set to <b>TRUE</b> when creating a NET_BUFFER_LIST structure pool. In this case,
    a NET_BUFFER structure is preallocated with each NET_BUFFER_LIST structure that the caller allocates from
    the pool. You can call the 
    <a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
    NdisAllocateNetBufferAndNetBufferList</a> function or the 
    <a href="https://msdn.microsoft.com/9c821aac-9abd-4041-a15e-64306ada1c02">
    NdisAllocateNetBufferList</a> function to allocate NET_BUFFER_LIST structures from such a pool. Call 
    <b>NdisAllocateNetBufferAndNetBufferList</b> only if 
    <b>fAllocateNetBuffer</b> is <b>TRUE</b> and 
    <b>DataSize</b> is zero.</p>

<p>You can also call 
    <b>NdisAllocateNetBufferListPool</b> and set the 
    <b>DataSize</b> member to a nonzero value when creating a NET_BUFFER_LIST structure pool. In this case, a
    NET_BUFFER structure, MDL, and data are preallocated with each NET_BUFFER_LIST structure that the caller
    allocates from the pool.</p>

<p>NET_BUFFER structures, MDLs, and data buffers that are allocated with 
    <a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
    NdisAllocateNetBufferAndNetBufferList</a> or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561609">NdisAllocateNetBufferList</a> should
    not be freed separate from the NET_BUFFER_LIST structure. Such structures are freed with the
    NET_BUFFER_LIST structure when you call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a> function.</p>

<p>Call the 
    <a href="https://msdn.microsoft.com/811df5ea-f5e6-4986-adc0-c5fa95e5f072">
    NdisFreeNetBufferListPool</a> function to free a NET_BUFFER_LIST structure pool.</p>

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
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.sys</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561609">NdisAllocateNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
   NdisAllocateNetBufferAndNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562590">NdisFreeNetBufferListPool</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568389">NET_BUFFER_LIST_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh205394">NET_BUFFER_LIST_POOL_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisAllocateNetBufferListPool function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
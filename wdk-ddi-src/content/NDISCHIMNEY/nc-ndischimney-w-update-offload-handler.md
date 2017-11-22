---
UID: NC.ndischimney.W_UPDATE_OFFLOAD_HANDLER
title: W_UPDATE_OFFLOAD_HANDLER
author: windows-driver-content
description: The MiniportUpdateOffload function updates previously offloaded TCP chimney state objects.
old-location: netvista\miniportupdateoffload.htm
ms.assetid: b98b2e21-8b28-4da0-9cc9-6fa8cb6e5be7
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndischimney.h
req.include-header: Ndischimney.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MiniportUpdateOffload
req.alt-loc: Ndischimney.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level
ms.keywords: BINARY_DATA, BINARY_DATA
req.iface: 
---

# W_UPDATE_OFFLOAD_HANDLER callback



## -description
<p class="CCE_Message">[The TCP chimney offload feature is deprecated and should not be used.]</p>
<p>The 
  <i>MiniportUpdateOffload</i> function updates previously offloaded TCP chimney state objects.</p>


## -prototype

````
W_UPDATE_OFFLOAD_HANDLER MiniportUpdateOffload;

VOID MiniportUpdateOffload(
  _In_ NDIS_HANDLE              MiniportAdapterContext,
  _In_ PNDIS_OFFLOAD_BLOCK_LIST OffloadBlockList
)
{ ... }
````


## -parameters
<dl>

### -param <i>MiniportAdapterContext</i> [in]

<dd>
<p>The handle to an offload target-allocated context area in which the offload target maintains state
     information about this instance of the adapter. The offload target provided this handle to NDIS when it
     called 
     <a href="https://msdn.microsoft.com/861626af-23ea-40dc-a91a-7da42d4b0a1c">
     NdisMSetMiniportAttributes</a> from its 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">
     MiniportInitializeEx</a> function.</p>
</dd>

### -param <i>OffloadBlockList</i> [in]

<dd>
<p>A pointer to an 
     <a href="https://msdn.microsoft.com/ebc98e65-5d11-4c3d-aea1-dfad1434c093">
     NDIS_MINIPORT_OFFLOAD_BLOCK_LIST</a> structure, which can be the root of a linked list of such
     structures. These structures identify the offloaded state objects that are being updated. Only cached
     variables are updated.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Only cached variables are updated.</p>

<p>The 
    <i>MiniportUpdateOffload</i> function stores the 
    <i>MiniportAdapterContext</i> handle and the 
    <i>OffloadBlockList</i> pointer and then returns. The offload target always completes the update operation
    asynchronously by calling the 
    <a href="https://msdn.microsoft.com/aa2c549c-eb16-4d59-9280-1913c8c0266a">
    NdisMUpdateOffloadComplete</a> function. The 
    <i>OffloadBlockList</i> pointer points to an NDIS_MINIPORT_OFFLOAD_BLOCK_LIST structure that can either be
    a stand-alone structure or the root block list in an 
    <a href="NULL">offload state tree</a> that contains multiple
    NDIS_MINIPORT_OFFLOAD_BLOCK_LIST structures. Such block lists, as well as any 
    <a href="NULL">offload state structures</a> that are
    associated with them, are valid until the miniport driver calls the 
    <b>
    NdisMUpdateOffloadComplete</b> function.</p>

<p>Before the 
    <i>MiniportUpdateOffload</i> function returns, the offload target uses the offload state tree passed to
    the 
    <i>MiniportUpdateOffload</i> function to update offloaded state:</p>

<p>The offload target copies the variable values from any state structures in the tree to the
      corresponding 
      <a href="netvista.offload_state_objects">offloaded state objects</a>. Only CACHED
      variables are updated.</p>

<p>The tree might indicate that path-to-neighbor links must be updated. For more information, see 
      <a href="netvista.linking_path_state_objects_to_a_new_neighbor_state_object">Linking
      Path State Objects to a New Neighbor State Object</a>. In this case, the offload target must update
      its internal representation of offloaded state to reflect the updated links.</p>

<p>Only cached variables are updated.</p>

<p>The 
    <i>MiniportUpdateOffload</i> function stores the 
    <i>MiniportAdapterContext</i> handle and the 
    <i>OffloadBlockList</i> pointer and then returns. The offload target always completes the update operation
    asynchronously by calling the 
    <a href="https://msdn.microsoft.com/aa2c549c-eb16-4d59-9280-1913c8c0266a">
    NdisMUpdateOffloadComplete</a> function. The 
    <i>OffloadBlockList</i> pointer points to an NDIS_MINIPORT_OFFLOAD_BLOCK_LIST structure that can either be
    a stand-alone structure or the root block list in an 
    <a href="NULL">offload state tree</a> that contains multiple
    NDIS_MINIPORT_OFFLOAD_BLOCK_LIST structures. Such block lists, as well as any 
    <a href="NULL">offload state structures</a> that are
    associated with them, are valid until the miniport driver calls the 
    <b>
    NdisMUpdateOffloadComplete</b> function.</p>

<p>Before the 
    <i>MiniportUpdateOffload</i> function returns, the offload target uses the offload state tree passed to
    the 
    <i>MiniportUpdateOffload</i> function to update offloaded state:</p>

<p>The offload target copies the variable values from any state structures in the tree to the
      corresponding 
      <a href="netvista.offload_state_objects">offloaded state objects</a>. Only CACHED
      variables are updated.</p>

<p>The tree might indicate that path-to-neighbor links must be updated. For more information, see 
      <a href="netvista.linking_path_state_objects_to_a_new_neighbor_state_object">Linking
      Path State Objects to a New Neighbor State Object</a>. In this case, the offload target must update
      its internal representation of offloaded state to reflect the updated links.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndischimney.h (include Ndischimney.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ebc98e65-5d11-4c3d-aea1-dfad1434c093">
   NDIS_MINIPORT_OFFLOAD_BLOCK_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563672">NdisMSetMiniportAttributes</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563694">NdisMUpdateOffloadComplete</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20W_UPDATE_OFFLOAD_HANDLER callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
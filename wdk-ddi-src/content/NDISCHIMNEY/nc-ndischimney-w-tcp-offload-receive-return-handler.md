---
UID: NC.ndischimney.W_TCP_OFFLOAD_RECEIVE_RETURN_HANDLER
title: W_TCP_OFFLOAD_RECEIVE_RETURN_HANDLER
author: windows-driver-content
description: NDIS calls the MiniportTcpOffloadReceiveReturn function to return ownership of NET_BUFFER_LIST and associated structures to an offload target.
old-location: netvista\miniporttcpoffloadreceivereturn.htm
ms.assetid: b746f58d-d029-4fcd-a59d-baba037fc38e
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
req.alt-api: MiniportTcpOffloadReceiveReturn
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

# W_TCP_OFFLOAD_RECEIVE_RETURN_HANDLER callback



## -description
<p class="CCE_Message">[The TCP chimney offload feature is deprecated and should not be used.]</p>
<p>NDIS calls the 
  <i>MiniportTcpOffloadReceiveReturn</i> function to return ownership of 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> and associated structures to
  an offload target.</p>


## -prototype

````
W_TCP_OFFLOAD_RECEIVE_RETURN_HANDLER MiniportTcpOffloadReceiveReturn;

NDIS_STATUS MiniportTcpOffloadReceiveReturn(
  _In_ NDIS_HANDLE      MiniportAdapterContext,
  _In_ PNET_BUFFER_LIST NetBufferList
)
{ ... }
````


## -parameters
<dl>

### -param <i>MiniportAdapterContext</i> [in]

<dd>
<p>The handle to an offload-target allocated context area in which the offload target maintains state
     information about this instance of the adapter. The miniport driver provided this handle to NDIS when it
     called 
     <a href="https://msdn.microsoft.com/861626af-23ea-40dc-a91a-7da42d4b0a1c">
     NdisMSetMiniportAttributes</a> from its 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">
     MiniportInitializeEx</a> function.</p>
</dd>

### -param <i>NetBufferList</i> [in]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure. This structure
     can be a stand-alone structure or the first structure in a linked list of NET_BUFFER_LIST structures.
     The linked list can contain NET_BUFFER_LIST structures from one or more calls to the 
     <a href="https://msdn.microsoft.com/a45dede9-6559-4207-a49f-d9627054433a">
     NdisTcpOffloadReceiveHandler</a> function.</p>
</dd>
</dl>

## -returns
<p>The 
     <i>MiniportTcpOffloadReceiveReturn</i> function should always succeed. Therefore, the 
     <i>MiniportTcpOffloadReceiveReturn</i> function should always return NDIS_STATUS_SUCCESS.</p>

## -remarks
<p>NDIS calls the 
    <i>MiniportTcpOffloadReceiveReturn</i> function to return ownership of NET_BUFFER_LIST structures and
    associated structures that the offload target passed in one or more previous calls to the 
    <a href="https://msdn.microsoft.com/a45dede9-6559-4207-a49f-d9627054433a">
    NdisTcpOffloadReceiveHandler</a> function.</p>

<p>The 
    <i>MiniportTcpOffloadReceiveReturn</i> function can prepare a returned NET_BUFFER_LIST structure for use
    in a subsequent receive indication. Although the 
    <i>MiniportTcpOffloadReceiveReturn</i> function can return the NET_BUFFER_LIST structures to a pool (for
    example, it could call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a> function), it
    can be more efficient to reuse the structures without returning them to the pool.</p>

<p>Note that the offload target driver should not unload and the offload target adapter must not be
    closed until all indicated receive buffers have been returned.</p>

<p>NDIS calls the 
    <i>MiniportTcpOffloadReceiveReturn</i> function to return ownership of NET_BUFFER_LIST structures and
    associated structures that the offload target passed in one or more previous calls to the 
    <a href="https://msdn.microsoft.com/a45dede9-6559-4207-a49f-d9627054433a">
    NdisTcpOffloadReceiveHandler</a> function.</p>

<p>The 
    <i>MiniportTcpOffloadReceiveReturn</i> function can prepare a returned NET_BUFFER_LIST structure for use
    in a subsequent receive indication. Although the 
    <i>MiniportTcpOffloadReceiveReturn</i> function can return the NET_BUFFER_LIST structures to a pool (for
    example, it could call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a> function), it
    can be more efficient to reuse the structures without returning them to the pool.</p>

<p>Note that the offload target driver should not unload and the offload target adapter must not be
    closed until all indicated receive buffers have been returned.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563672">NdisMSetMiniportAttributes</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564606">NdisTcpOffloadReceiveHandler</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20W_TCP_OFFLOAD_RECEIVE_RETURN_HANDLER callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
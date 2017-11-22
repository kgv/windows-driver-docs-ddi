---
UID: NF.ndis.NdisMIndicateStatusEx
title: NdisMIndicateStatusEx
author: windows-driver-content
description: The NdisMIndicateStatusEx function reports a change in the status of a miniport adapter.
old-location: netvista\ndismindicatestatusex.htm
ms.assetid: df857349-4ae1-470b-b41a-ff014f40b79b
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
req.alt-api: NdisMIndicateStatusEx
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_StatusIndication_Function, NdisMIndicateStatusEx, WlanAssociation, WlanConnectionRoaming, WlanDisassociation, WlanTimedAssociation, WlanTimedConnectionRoaming, WlanTimedConnectRequest, WlanTimedLinkQuality, WlanTimedScan
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisMIndicateStatusEx
req.iface: 
---

# NdisMIndicateStatusEx function



## -description
<p>The 
  <b>NdisMIndicateStatusEx</b> function reports a change in the status of a miniport adapter.</p>


## -syntax

````
VOID NdisMIndicateStatusEx(
  _In_ NDIS_HANDLE             MiniportAdapterHandle,
  _In_ PNDIS_STATUS_INDICATION StatusIndication
);
````


## -parameters
<dl>

### -param <i>MiniportAdapterHandle</i> [in]

<dd>
<p>The miniport adapter handle that NDIS passed at the 
     <i>MiniportAdapterHandle</i> parameter of the 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">
     MiniportInitializeEx</a> function.</p>
</dd>

### -param <i>StatusIndication</i> [in]

<dd>
<p>A pointer to an 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff567373">NDIS_STATUS_INDICATION</a> structure
     that contains the status information.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>When a miniport driver calls 
    <b>NdisMIndicateStatusEx</b>, NDIS calls each bound protocol driver's 
    <a href="https://msdn.microsoft.com/5bc5a24f-5f28-4502-8776-b1cf15fd8283">ProtocolStatusEx</a> function. This allows
    a bound protocol driver to log the change in status of an underlying miniport adapter or to take
    action.</p>

<p>A miniport driver can call 
    <b>NdisMIndicateStatusEx</b> after setting its registration attributes even if the driver is still in the
    context of the 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function. The
    driver must not call 
    <b>NdisMIndicateStatusEx</b> after it returns from the 
    <a href="https://msdn.microsoft.com/b8d452b4-bef3-4991-87cf-fac15bedfde4">MiniportHaltEx</a> function.</p>

<p>When a miniport driver calls 
    <b>NdisMIndicateStatusEx</b>, NDIS calls each bound protocol driver's 
    <a href="https://msdn.microsoft.com/5bc5a24f-5f28-4502-8776-b1cf15fd8283">ProtocolStatusEx</a> function. This allows
    a bound protocol driver to log the change in status of an underlying miniport adapter or to take
    action.</p>

<p>A miniport driver can call 
    <b>NdisMIndicateStatusEx</b> after setting its registration attributes even if the driver is still in the
    context of the 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function. The
    driver must not call 
    <b>NdisMIndicateStatusEx</b> after it returns from the 
    <a href="https://msdn.microsoft.com/b8d452b4-bef3-4991-87cf-fac15bedfde4">MiniportHaltEx</a> function.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548011">Irql_StatusIndication_Function</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff563600">NdisMIndicateStatusEx</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305122">WlanAssociation</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305123">WlanConnectionRoaming</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305124">WlanDisassociation</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305125">WlanTimedAssociation</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305126">WlanTimedConnectionRoaming</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305127">WlanTimedConnectRequest</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305128">WlanTimedLinkQuality</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn305129">WlanTimedScan</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b8d452b4-bef3-4991-87cf-fac15bedfde4">MiniportHaltEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567373">NDIS_STATUS_INDICATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/5bc5a24f-5f28-4502-8776-b1cf15fd8283">ProtocolStatusEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMIndicateStatusEx function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.ndis.NdisFNetPnPEvent
title: NdisFNetPnPEvent
author: windows-driver-content
description: A filter driver can call the NdisFNetPnPEvent function to forward a network Plug and Play (PnP) or Power Management event to overlying drivers.
old-location: netvista\ndisfnetpnpevent.htm
ms.assetid: 383f9dcb-68ba-4323-b25f-668169043f35
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisFNetPnPEvent
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Filter_Driver_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisFNetPnPEvent
req.iface: 
---

# NdisFNetPnPEvent function



## -description
<p>A filter driver can call the 
  <b>NdisFNetPnPEvent</b> function to forward a network Plug and Play (PnP) or Power Management event to
  overlying drivers.</p>


## -syntax

````
NDIS_STATUS NdisFNetPnPEvent(
  _In_ NDIS_HANDLE                 FilterModuleContext,
  _In_ PNET_PNP_EVENT_NOTIFICATION NetPnPEvent
);
````


## -parameters
<dl>

### -param <i>FilterModuleContext</i> [in]

<dd>
<p>A handle to the context area for the filter module. The filter driver created and initialized this
     context area in the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a> function.</p>
</dd>

### -param <i>NetPnPEvent</i> [in]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/58d3baf3-a1fa-42ae-b795-2774a148aeda">
     NET_PNP_EVENT_NOTIFICATION</a> structure, which describes the network PnP event or Power Management
     event being forwarded by the filter driver.</p>
</dd>
</dl>

## -returns
<p><b>NdisFNetPnPEvent</b> can return either of the following:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p>The overlying driver succeeded in processing the PnP event.</p><dl>
<dt><b>NDIS_STATUS_FAILURE</b></dt>
</dl><p>The overlying driver failed the PnP event.</p>

<p> </p>

## -remarks
<p>NDIS calls a filter driver's 
    <a href="https://msdn.microsoft.com/5c52b2d2-3fba-4d28-8172-7b6854386061">FilterNetPnPEvent</a> function to notify
    the filter driver of network PnP and Power Management events.</p>

<p>Filter drivers can forward these notifications to overlying drivers. To forward a request, call the 
    <b>NdisFNetPnPEvent</b> function from 
    <i>FilterNetPnPEvent</i>.</p>

<p>NDIS calls a filter driver's 
    <a href="https://msdn.microsoft.com/5c52b2d2-3fba-4d28-8172-7b6854386061">FilterNetPnPEvent</a> function to notify
    the filter driver of network PnP and Power Management events.</p>

<p>Filter drivers can forward these notifications to overlying drivers. To forward a request, call the 
    <b>NdisFNetPnPEvent</b> function from 
    <i>FilterNetPnPEvent</i>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547930">Irql_Filter_Driver_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/5c52b2d2-3fba-4d28-8172-7b6854386061">FilterNetPnPEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/238bfa21-a971-4fe4-a774-6ba834efc3c5">FilterOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568752">NET_PNP_EVENT_NOTIFICATION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisFNetPnPEvent function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
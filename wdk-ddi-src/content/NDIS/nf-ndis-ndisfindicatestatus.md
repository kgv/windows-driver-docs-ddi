---
UID: NF.ndis.NdisFIndicateStatus
title: NdisFIndicateStatus
author: windows-driver-content
description: The NdisFIndicateStatus function passes on a filtered status indication from an underlying driver or originates a status indication.
old-location: netvista\ndisfindicatestatus.htm
ms.assetid: fd81d777-8479-41e3-8f71-e5f4134b60a0
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
req.alt-api: NdisFIndicateStatus
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_StatusIndication_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisFIndicateStatus
req.iface: 
---

# NdisFIndicateStatus function



## -description
<p>The 
  <b>NdisFIndicateStatus</b> function passes on a filtered status indication from an underlying driver or
  originates a status indication.</p>


## -syntax

````
VOID NdisFIndicateStatus(
  _In_ NDIS_HANDLE             NdisFilterHandle,
  _In_ PNDIS_STATUS_INDICATION StatusIndication
);
````


## -parameters
<dl>

### -param <i>NdisFilterHandle</i> [in]

<dd>
<p>The NDIS handle that identifies this filter module. NDIS passed the handle to the filter driver in
     a call to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a> function.</p>
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
<p>Filter drivers can call 
    <b>NdisFIndicateStatus</b> from the 
    <a href="https://msdn.microsoft.com/051ce37c-a7a5-4367-9495-023fc51349ba">FilterStatus</a> function, to pass on a
    filtered status indication to overlying drivers.</p>

<p>To originate status indications, filter drivers call 
    <b>NdisFIndicateStatus</b> without a prior NDIS call to 
    <i>FilterStatus</i>.</p>

<p>A filter driver can call 
    <b>NdisFIndicateStatus</b> after setting its registration attributes and the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562619">NdisFSetAttributes</a> function returns.
    The driver must not call 
    <b>NdisFIndicateStatus</b> after it returns from the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff540475">FilterDetach</a> function.</p>

<p>Filter drivers can call 
    <b>NdisFIndicateStatus</b> from the 
    <a href="https://msdn.microsoft.com/051ce37c-a7a5-4367-9495-023fc51349ba">FilterStatus</a> function, to pass on a
    filtered status indication to overlying drivers.</p>

<p>To originate status indications, filter drivers call 
    <b>NdisFIndicateStatus</b> without a prior NDIS call to 
    <i>FilterStatus</i>.</p>

<p>A filter driver can call 
    <b>NdisFIndicateStatus</b> after setting its registration attributes and the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562619">NdisFSetAttributes</a> function returns.
    The driver must not call 
    <b>NdisFIndicateStatus</b> after it returns from the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff540475">FilterDetach</a> function.</p>

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548011">Irql_StatusIndication_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540475">FilterDetach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/051ce37c-a7a5-4367-9495-023fc51349ba">FilterStatus</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567373">NDIS_STATUS_INDICATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562619">NdisFSetAttributes</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisFIndicateStatus function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
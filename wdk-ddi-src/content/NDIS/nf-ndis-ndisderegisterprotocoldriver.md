---
UID: NF.ndis.NdisDeregisterProtocolDriver
title: NdisDeregisterProtocolDriver
author: windows-driver-content
description: A protocol driver calls the NdisDeregisterProtocolDriver function to release the resources that NDIS allocated when the driver called the NdisRegisterProtocolDriver function.
old-location: netvista\ndisderegisterprotocoldriver.htm
ms.assetid: 792f8f89-ff2c-45d1-bb15-9fcdafd14231
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
req.alt-api: NdisDeregisterProtocolDriver
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Protocol_Driver_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisDeregisterProtocolDriver
req.iface: 
---

# NdisDeregisterProtocolDriver function



## -description
<p>A protocol driver calls the
  <b>NdisDeregisterProtocolDriver</b> function to release the resources that NDIS allocated when the driver
  called the 
  <a href="https://msdn.microsoft.com/b48571eb-13a2-4541-80ac-c8d31f378d37">
  NdisRegisterProtocolDriver</a> function.</p>


## -syntax

````
VOID NdisDeregisterProtocolDriver(
  _In_ NDIS_HANDLE NdisProtocolHandle
);
````


## -parameters
<dl>

### -param <i>NdisProtocolHandle</i> [in]

<dd>
<p>The handle returned by the 
     <a href="https://msdn.microsoft.com/b48571eb-13a2-4541-80ac-c8d31f378d37">
     NdisRegisterProtocolDriver</a> function.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Registered protocol drivers typically call 
    <b>NdisDeregisterProtocolDriver</b> when the driver's 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564886">Unload</a> routine has been called or after errors occur
    in the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine. Protocol drivers must not
    call 
    <b>NdisDeregisterProtocolDriver</b> from any entry point that NDIS calls. Calling 
    <b>NdisDeregisterProtocolDriver</b> from such an entry point could cause a deadlock.</p>

<p>If a protocol driver has open bindings, its call to 
    <b>NdisDeregisterProtocolDriver</b> causes NDIS to call the protocol driver's 
    <a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">
    ProtocolUnbindAdapterEx</a> function once for each open binding. NDIS calls 
    <i>ProtocolUnbindAdapterEx</i> within the context of the 
    <b>NdisDeregisterProtocolDriver</b> call.</p>

<p>After any outstanding bindings have been closed, 
    <b>NdisDeregisterProtocolDriver</b> releases all of the resources that NDIS allocated to track bindings
    and filters for the protocol driver.</p>

<p>Registered protocol drivers typically call 
    <b>NdisDeregisterProtocolDriver</b> when the driver's 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564886">Unload</a> routine has been called or after errors occur
    in the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine. Protocol drivers must not
    call 
    <b>NdisDeregisterProtocolDriver</b> from any entry point that NDIS calls. Calling 
    <b>NdisDeregisterProtocolDriver</b> from such an entry point could cause a deadlock.</p>

<p>If a protocol driver has open bindings, its call to 
    <b>NdisDeregisterProtocolDriver</b> causes NDIS to call the protocol driver's 
    <a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">
    ProtocolUnbindAdapterEx</a> function once for each open binding. NDIS calls 
    <i>ProtocolUnbindAdapterEx</i> within the context of the 
    <b>NdisDeregisterProtocolDriver</b> call.</p>

<p>After any outstanding bindings have been closed, 
    <b>NdisDeregisterProtocolDriver</b> releases all of the resources that NDIS allocated to track bindings
    and filters for the protocol driver.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547996">Irql_Protocol_Driver_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564520">NdisRegisterProtocolDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">ProtocolUnbindAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564886">Unload</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisDeregisterProtocolDriver function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.ndis.NdisOpenAdapterEx
title: NdisOpenAdapterEx
author: windows-driver-content
description: A protocol driver calls the NdisOpenAdapterEx function from its ProtocolBindAdapterEx function to set up a binding between the protocol driver and an underlying driver.
old-location: netvista\ndisopenadapterex.htm
ms.assetid: 2dc356e6-a2ef-4b43-abe5-7c5058c15cf5
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
req.alt-api: NdisOpenAdapterEx
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
ms.keywords: NdisOpenAdapterEx
req.iface: 
---

# NdisOpenAdapterEx function



## -description
<p>A protocol driver calls the
  <b>NdisOpenAdapterEx</b> function from its 
  <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> function to
  set up a binding between the protocol driver and an underlying driver.</p>


## -syntax

````
NDIS_STATUS NdisOpenAdapterEx(
  _In_  NDIS_HANDLE           NdisProtocolHandle,
  _In_  NDIS_HANDLE           ProtocolBindingContext,
  _In_  PNDIS_OPEN_PARAMETERS OpenParameters,
  _In_  NDIS_HANDLE           BindContext,
  _Out_ PNDIS_HANDLE          NdisBindingHandle
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

### -param <i>ProtocolBindingContext</i> [in]

<dd>
<p>The handle for a caller-supplied context area in which the protocol driver maintains state
     information for this binding.</p>
</dd>

### -param <i>OpenParameters</i> [in]

<dd>
<p>A pointer to an 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566734">NDIS_OPEN_PARAMETERS</a> structure that is
     set up by the caller.</p>
</dd>

### -param <i>BindContext</i> [in]

<dd>
<p>The handle that identifies the NDIS context area for the bind operation. NDIS passed this handle
     to the 
     <i>BindContext</i> parameter of the 
     <i>ProtocolBindAdapterEx</i> function.</p>
</dd>

### -param <i>NdisBindingHandle</i> [out]

<dd>
<p>A pointer to a caller-supplied variable. NDIS writes a handle at 
     <i>NdisBindingHandle</i> that identifies the binding between the caller and the miniport adapter
     specified in the 
     <b>AdapterName</b> member at 
     <i>OpenParameters</i> . The caller uses this handle in subsequent calls to 
     <b>Ndis<i>Xxx</i></b> functions.</p>
</dd>
</dl>

## -returns
<p><b>NdisOpenAdapterEx</b> returns one of the following status values:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p><b>NdisOpenAdapterEx</b> successfully completed the open operation.</p><dl>
<dt><b>NDIS_STATUS_PENDING</b></dt>
</dl><p><b>NdisOpenAdapterEx</b> did not complete the open operation. NDIS later calls the protocol driver's 
       <a href="https://msdn.microsoft.com/59d18822-8ce2-4506-90d7-9f1cdc7a9e10">
       ProtocolOpenAdapterCompleteEx</a> function to complete the open operation.</p><dl>
<dt><b>NDIS_STATUS_RESOURCES</b></dt>
</dl><p><b>NdisOpenAdapterEx</b> failed due to insufficient resources.</p><dl>
<dt><b>NDIS_STATUS_ADAPTER_NOT_FOUND</b></dt>
</dl><p><b>NdisOpenAdapterEx</b> failed because a miniport adapter specified in the 
       <b>AdapterName</b> member at 
       <i>OpenParameters</i> could not be found.</p><dl>
<dt><b>NDIS_STATUS_UNSUPPORTED_MEDIA</b></dt>
</dl><p><b>NdisOpenAdapterEx</b> failed because the array specified in the 
       <b>MediumArray</b> member at 
       <i>OpenParameters</i> did not include a medium type that NDIS or the underlying driver supports.</p><dl>
<dt><b>NDIS_STATUS_FAILURE</b></dt>
</dl><p><b>NdisOpenAdapterEx</b> failed for reasons other than those in the preceding list.</p>

<p> </p>

## -remarks
<p>A protocol driver must call 
    <b>NdisOpenAdapterEx</b> from its 
    <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> function.
    NDIS fails any attempt to call 
    <b>NdisOpenAdapterEx</b> outside the context of 
    <i>ProtocolBindAdapterEx</i>.</p>

<p>If 
    <b>NdisOpenAdapterEx</b> returns NDIS_STATUS_PENDING, the caller must not use the values at 
    <i>NdisBindingHandle</i> and the 
    <b>SelectedMediumIndex</b> member at 
    <i>OpenParameters</i> until NDIS calls the 
    <a href="https://msdn.microsoft.com/59d18822-8ce2-4506-90d7-9f1cdc7a9e10">
    ProtocolOpenAdapterCompleteEx</a> function.</p>

<p>The string at 
    <b>AdapterName</b> must remain valid only until 
    <b>NdisOpenAdapterEx</b> returns. Therefore, in the case that 
    <b>NdisOpenAdapterEx</b> returns NDIS_STATUS_PENDING, the driver is not required to continue to retain
    this string after 
    <b>NdisOpenAdapterEx</b> returns.</p>

<p>After the open operation completes successfully, the caller can use the value that NDIS returned in
    the 
    <i>NdisBindingHandle</i> in subsequent calls to 
    <b>Ndis<i>Xxx</i></b> functions. The caller can use the 
    <b>SelectedMediumIndex</b> member of the 
    <i>OpenParameters</i> parameter to determine how it should interact with the underlying driver.</p>

<p>A protocol driver must call 
    <b>NdisOpenAdapterEx</b> from its 
    <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> function.
    NDIS fails any attempt to call 
    <b>NdisOpenAdapterEx</b> outside the context of 
    <i>ProtocolBindAdapterEx</i>.</p>

<p>If 
    <b>NdisOpenAdapterEx</b> returns NDIS_STATUS_PENDING, the caller must not use the values at 
    <i>NdisBindingHandle</i> and the 
    <b>SelectedMediumIndex</b> member at 
    <i>OpenParameters</i> until NDIS calls the 
    <a href="https://msdn.microsoft.com/59d18822-8ce2-4506-90d7-9f1cdc7a9e10">
    ProtocolOpenAdapterCompleteEx</a> function.</p>

<p>The string at 
    <b>AdapterName</b> must remain valid only until 
    <b>NdisOpenAdapterEx</b> returns. Therefore, in the case that 
    <b>NdisOpenAdapterEx</b> returns NDIS_STATUS_PENDING, the driver is not required to continue to retain
    this string after 
    <b>NdisOpenAdapterEx</b> returns.</p>

<p>After the open operation completes successfully, the caller can use the value that NDIS returned in
    the 
    <i>NdisBindingHandle</i> in subsequent calls to 
    <b>Ndis<i>Xxx</i></b> functions. The caller can use the 
    <b>SelectedMediumIndex</b> member of the 
    <i>OpenParameters</i> parameter to determine how it should interact with the underlying driver.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566734">NDIS_OPEN_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564520">NdisRegisterProtocolDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/59d18822-8ce2-4506-90d7-9f1cdc7a9e10">
   ProtocolOpenAdapterCompleteEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisOpenAdapterEx function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
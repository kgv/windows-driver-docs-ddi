---
UID: NF.ndis.NdisOpenConfigurationKeyByName
title: NdisOpenConfigurationKeyByName
author: windows-driver-content
description: The NdisOpenConfigurationKeyByName function opens a named subkey of a given open registry key that is designated by a caller-supplied handle.
old-location: netvista\ndisopenconfigurationkeybyname.htm
ms.assetid: 9ce7f40f-28f1-4303-9f7a-24ff1213bab1
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   
   NdisOpenConfigurationKeyByName (NDIS 5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   
   NdisOpenConfigurationKeyByName (NDIS 5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisOpenConfigurationKeyByName
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Miscellaneous_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: < DISPATCH_LEVEL
ms.keywords: NdisOpenConfigurationKeyByName
req.iface: 
---

# NdisOpenConfigurationKeyByName function



## -description
<p>The 
  <b>NdisOpenConfigurationKeyByName</b> function opens a named subkey of a given open registry key that is
  designated by a caller-supplied handle.</p>


## -syntax

````
VOID NdisOpenConfigurationKeyByName(
  _Out_ PNDIS_STATUS Status,
  _In_  NDIS_HANDLE  ConfigurationHandle,
  _In_  PNDIS_STRING SubKeyName,
  _Out_ PNDIS_HANDLE SubKeyHandle
);
````


## -parameters
<dl>

### -param <i>Status</i> [out]

<dd>
<p>A pointer to a caller-supplied variable in which this function returns the status of its attempt
     to open the registry key. Possible return values are one of the following:
     </p>
<p></p>
<dl>

### -param <a id="NDIS_STATUS_SUCCESS"></a><a id="ndis_status_success"></a>NDIS_STATUS_SUCCESS

<dd>
<p>NDIS has initialized accessed to the subkey specified by 
       <i>SubKeyName</i> .</p>
</dd>

### -param <a id="NDIS_STATUS_FAILURE"></a><a id="ndis_status_failure"></a>NDIS_STATUS_FAILURE

<dd>
<p>The key could not be opened.</p>
</dd>
</dl>
</dd>

### -param <i>ConfigurationHandle</i> [in]

<dd>
<p>The handle to a registry key for which a subkey should be opened. Typically, 
     <i>ConfigurationHandle</i> is returned by the 
     <a href="https://msdn.microsoft.com/76539106-6d8d-4a80-9c74-a6a4ca37c40e">
     NdisOpenConfigurationEx</a> function.</p>
</dd>

### -param <i>SubKeyName</i> [in]

<dd>
<p>A pointer to an NDIS_STRING type containing a caller-supplied, counted string in the
     system-default character set that specifies the name of the registry subkey to open. For Microsoft
     Windows 2000 and later drivers, this string contains Unicode characters. That is, for Windows 2000 and
     later, NDIS defines the NDIS_STRING type as a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> type.</p>
</dd>

### -param <i>SubKeyHandle</i> [out]

<dd>
<p>A pointer to a caller-supplied variable in which this function returns a handle to the opened
     subkey if this call is successful.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>NdisOpenConfigurationKeyByName</b> allows a driver to access configuration information that is stored
    in a named subkey in the registry.</p>

<p>Note that the 
    <i>ConfigurationHandle</i> passed in to 
    <b>NdisOpenConfigurationKeyByName</b> can be any valid handle to a registry key already opened by the
    caller. 
    <b>NdisOpenConfigurationKeyByName</b> returns configuration information for subkeys relative to any valid 
    <i>ConfigurationHandle</i> .</p>

<p>After a driver has consumed and, possibly, modified the registry configuration information, it must
    call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561642">NdisCloseConfiguration</a> function to
    release the handle that was obtained from 
    <b>NdisOpenConfigurationKeyByName</b>. 
    <b>NdisCloseConfiguration</b> also frees any temporary storage that NDIS allocated in the driver's calls
    to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564511">NdisReadConfiguration</a>, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564512">NdisReadNetworkAddress</a>, or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564659">NdisWriteConfiguration</a> functions
    with the 
    <i>SubKeyHandle</i> that 
    <b>NdisOpenConfigurationKeyByName</b> returned.</p>

<p><b>NdisOpenConfigurationKeyByName</b> allows a driver to access configuration information that is stored
    in a named subkey in the registry.</p>

<p>Note that the 
    <i>ConfigurationHandle</i> passed in to 
    <b>NdisOpenConfigurationKeyByName</b> can be any valid handle to a registry key already opened by the
    caller. 
    <b>NdisOpenConfigurationKeyByName</b> returns configuration information for subkeys relative to any valid 
    <i>ConfigurationHandle</i> .</p>

<p>After a driver has consumed and, possibly, modified the registry configuration information, it must
    call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561642">NdisCloseConfiguration</a> function to
    release the handle that was obtained from 
    <b>NdisOpenConfigurationKeyByName</b>. 
    <b>NdisCloseConfiguration</b> also frees any temporary storage that NDIS allocated in the driver's calls
    to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564511">NdisReadConfiguration</a>, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564512">NdisReadNetworkAddress</a>, or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564659">NdisWriteConfiguration</a> functions
    with the 
    <i>SubKeyHandle</i> that 
    <b>NdisOpenConfigurationKeyByName</b> returned.</p>

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
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/a820440c-6186-4172-a567-843d89e49ad5">
   NdisOpenConfigurationKeyByName (NDIS 5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>
   NdisOpenConfigurationKeyByName (NDIS 5.1)</b>) in Windows XP.</p>
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
<p>&lt; DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547982">Irql_Miscellaneous_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540605">ANSI_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561642">NdisCloseConfiguration</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975122">NdisOpenConfigurationEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e405853a-cf25-4214-82a9-bc3d76334413">
   NdisOpenConfigurationKeyByIndex</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564511">NdisReadConfiguration</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564659">NdisWriteConfiguration</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisOpenConfigurationKeyByName function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
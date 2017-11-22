---
UID: NF.ndis.NdisWriteConfiguration
title: NdisWriteConfiguration
author: windows-driver-content
description: The NdisWriteConfiguration function writes a caller-supplied value for a specified entry into the registry. This function must be invoked serially with respect to itself and the NdisReadConfiguration function.
old-location: netvista\ndiswriteconfiguration.htm
ms.assetid: 63c94f4d-1c8c-43c2-ae58-993da42a80a4
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisWriteConfiguration (NDIS
   5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisWriteConfiguration (NDIS
   5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisWriteConfiguration
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
req.irql: PASSIVE_LEVEL
ms.keywords: NdisWriteConfiguration
req.iface: 
---

# NdisWriteConfiguration function



## -description
<p>The 
  <b>NdisWriteConfiguration</b> function writes a caller-supplied value for a specified entry into the
  registry. This function must be invoked serially with respect to itself and the <a href="https://msdn.microsoft.com/library/windows/hardware/ff564511">NdisReadConfiguration</a> function.</p>


## -syntax

````
VOID NdisWriteConfiguration(
  _Out_ PNDIS_STATUS                  Status,
  _In_  NDIS_HANDLE                   ConfigurationHandle,
  _In_  PNDIS_STRING                  Keyword,
  _In_  PNDIS_CONFIGURATION_PARAMETER ParameterValue
);
````


## -parameters
<dl>

### -param <i>Status</i> [out]

<dd>
<p>A pointer to a caller-supplied variable in which this function returns the status of the call as
     one of the following:
     </p>
<p></p>
<dl>

### -param <a id="NDIS_STATUS_SUCCESS"></a><a id="ndis_status_success"></a>NDIS_STATUS_SUCCESS

<dd>
<p>The supplied value at 
       <i>ParameterValue</i> was written into the registry. If this is a new entry, the name at 
       <i>Keyword</i> also was written into the registry.</p>
</dd>

### -param <a id="NDIS_STATUS_NOT_SUPPORTED"></a><a id="ndis_status_not_supported"></a>NDIS_STATUS_NOT_SUPPORTED

<dd>
<p>The supplied 
       <b>ParameterType</b> is invalid.</p>
</dd>

### -param <a id="NDIS_STATUS_RESOURCES"></a><a id="ndis_status_resources"></a>NDIS_STATUS_RESOURCES

<dd>
<p>NDIS could not allocate resources, usually enough memory, to transfer the requested information
       to the registry.</p>
</dd>

### -param <a id="NDIS_STATUS_FAILURE"></a><a id="ndis_status_failure"></a>NDIS_STATUS_FAILURE

<dd>
<p>The requested information could not be written.</p>
</dd>
</dl>
</dd>

### -param <i>ConfigurationHandle</i> [in]

<dd>
<p>The handle to a registry key that was returned by the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/hh975122">NdisOpenConfigurationEx</a>, 
     <a href="https://msdn.microsoft.com/e405853a-cf25-4214-82a9-bc3d76334413">
     NdisOpenConfigurationKeyByIndex</a>, or 
     <a href="https://msdn.microsoft.com/9ce7f40f-28f1-4303-9f7a-24ff1213bab1">
     NdisOpenConfigurationKeyByName</a> function.</p>
</dd>

### -param <i>Keyword</i> [in]

<dd>
<p>A pointer to an NDIS_STRING type describing a caller-supplied counted string, in the
     system-default character set, specifying the name of an entry for which to write the value. For
     Microsoft Windows 2000 and later drivers, this string contains Unicode characters. That is, for Windows
     2000 and later, NDIS defines the NDIS_STRING type as a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> type.</p>
</dd>

### -param <i>ParameterValue</i> [in]

<dd>
<p>Pointer to a caller-supplied 
     <a href="https://msdn.microsoft.com/80250799-4263-43c0-85d5-f1c1c1fb0bae">
     NDIS_CONFIGURATION_PARAMETER</a> structure.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>If an entry of the same name as at 
    <i>Keyword</i> already exists under the opened registry key, 
    <b>NdisWriteConfiguration</b> replaces its current value with the caller-supplied value. Otherwise, 
    <b>NdisWriteConfiguration</b> adds a new value entry with the given name and supplied value to the
    registry.</p>

<p>In the configuration registry of Windows 2000 and later versions, an NDIS 
    <i>Keyword</i> is a synonym for a
    <i>value entry name</i>. Such a name is a counted sequence of Unicode characters, terminated with a
    NUL.</p>

<p><b>NdisWriteConfiguration</b> buffers and copies the caller-supplied string at 
    <i>Keyword</i> and the caller-supplied data specified at 
    <i>ParameterValue</i> . This memory is freed when the driver releases the 
    <i>ConfigurationHandle</i> with the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561642">NdisCloseConfiguration</a> function.
    The caller of 
    <b>NdisWriteConfiguration</b> is responsible for releasing the buffered string at 
    <i>Keyword</i> and the memory allocated for the 
    <a href="https://msdn.microsoft.com/80250799-4263-43c0-85d5-f1c1c1fb0bae">
    NDIS_CONFIGURATION_PARAMETER</a> structure.</p>

<p>As an alternative to calling 
    <b>NdisWriteConfiguration</b>, every NDIS driver can set up configuration information in the registry for
    itself using the AddReg directive in the driver's INF file.</p>

<p>For more information about setup and installation files for Windows 2000 and later versions, see 
    <a href="devinst.overview_of_device_and_driver_installation">Device Installation
    Overview</a>.</p>

<p>If an entry of the same name as at 
    <i>Keyword</i> already exists under the opened registry key, 
    <b>NdisWriteConfiguration</b> replaces its current value with the caller-supplied value. Otherwise, 
    <b>NdisWriteConfiguration</b> adds a new value entry with the given name and supplied value to the
    registry.</p>

<p>In the configuration registry of Windows 2000 and later versions, an NDIS 
    <i>Keyword</i> is a synonym for a
    <i>value entry name</i>. Such a name is a counted sequence of Unicode characters, terminated with a
    NUL.</p>

<p><b>NdisWriteConfiguration</b> buffers and copies the caller-supplied string at 
    <i>Keyword</i> and the caller-supplied data specified at 
    <i>ParameterValue</i> . This memory is freed when the driver releases the 
    <i>ConfigurationHandle</i> with the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561642">NdisCloseConfiguration</a> function.
    The caller of 
    <b>NdisWriteConfiguration</b> is responsible for releasing the buffered string at 
    <i>Keyword</i> and the memory allocated for the 
    <a href="https://msdn.microsoft.com/80250799-4263-43c0-85d5-f1c1c1fb0bae">
    NDIS_CONFIGURATION_PARAMETER</a> structure.</p>

<p>As an alternative to calling 
    <b>NdisWriteConfiguration</b>, every NDIS driver can set up configuration information in the registry for
    itself using the AddReg directive in the driver's INF file.</p>

<p>For more information about setup and installation files for Windows 2000 and later versions, see 
    <a href="devinst.overview_of_device_and_driver_installation">Device Installation
    Overview</a>.</p>

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
   <a href="https://msdn.microsoft.com/c6d956fc-b634-4ca6-8597-ceeb1cd8d94f">NdisWriteConfiguration (NDIS
   5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisWriteConfiguration (NDIS
   5.1)</b>) in Windows XP.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564868">NDIS_CONFIGURATION_PARAMETER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8efdcf9f-df8c-4b3b-8b21-11a10a885322">
   NdisAnsiStringToUnicodeString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561642">NdisCloseConfiguration</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562577">NdisFreeMemory</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562604">NdisFreeString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562730">NdisInitAnsiString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562741">NdisInitializeString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562745">NdisInitUnicodeString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975122">NdisOpenConfigurationEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e405853a-cf25-4214-82a9-bc3d76334413">
   NdisOpenConfigurationKeyByIndex</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/9ce7f40f-28f1-4303-9f7a-24ff1213bab1">
   NdisOpenConfigurationKeyByName</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564511">NdisReadConfiguration</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/37ac55b8-093e-4bf4-9c66-05ab5fc7ebc9">
   NdisUnicodeStringToAnsiString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisWriteConfiguration function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
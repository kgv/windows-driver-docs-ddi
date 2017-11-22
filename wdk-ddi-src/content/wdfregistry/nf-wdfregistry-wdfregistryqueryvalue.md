---
UID: NF.wdfregistry.WdfRegistryQueryValue
title: WdfRegistryQueryValue
author: windows-driver-content
description: The WdfRegistryQueryValue method retrieves the data that is currently assigned to a specified registry value.
old-location: wdf\wdfregistryqueryvalue.htm
ms.assetid: 1d61e35a-64c6-42e0-b20d-969ded8b9750
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfregistry.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfRegistryQueryValue
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.dll (UMDF)
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfRegistryQueryValue
req.iface: 
req.product: Windows 10 or later.
---

# WdfRegistryQueryValue function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfRegistryQueryValue</b> method retrieves the data that is currently assigned to a specified registry value.</p>


## -syntax

````
NTSTATUS WdfRegistryQueryValue(
  _In_      WDFKEY           Key,
  _In_      PCUNICODE_STRING ValueName,
  _In_      ULONG            ValueLength,
  _Out_opt_ PVOID            Value,
  _Out_opt_ PULONG           ValueLengthQueried,
  _Out_opt_ PULONG           ValueType
);
````


## -parameters
<dl>

### -param <i>Key</i> [in]

<dd>
<p>A handle to a registry-key object that represents an opened registry key.</p>
</dd>

### -param <i>ValueName</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure that contains a value name. </p>
</dd>

### -param <i>ValueLength</i> [in]

<dd>
<p>The length, in bytes, of the buffer that <i>Value</i> points to.</p>
</dd>

### -param <i>Value</i> [out, optional]

<dd>
<p>A pointer to a driver-allocated buffer that receives the registry value's data. If this pointer is <b>NULL</b>, <b>WdfRegistryQueryValue</b> retrieves the data length but not the data.</p>
</dd>

### -param <i>ValueLengthQueried</i> [out, optional]

<dd>
<p>A pointer to a location that receives the registry value's data length. This pointer is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>ValueType</i> [out, optional]

<dd>
<p>A pointer to a location that receives the registry value's data type. For a list of data type values, see the <b>Type</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff553410">KEY_VALUE_BASIC_INFORMATION</a>. This pointer is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p><b>WdfRegistryQueryValue</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, the method might return one of the following values:</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549928">WdfRegistryQueryValue</a> was not called at IRQL = PASSIVE_LEVEL. </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid parameter was specified.</p><dl>
<dt><b>STATUS_ACCESS_DENIED</b></dt>
</dl><p>The driver did not open the registry key with KEY_QUERY_VALUE, KEY_READ, or KEY_ALL_ACCESS access.</p><dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl><p>The buffer that the <i>Value</i> parameter points to is too small, and only partial data has been written to the buffer.</p><dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl><p>The <i>Value</i> buffer is too small, and no data has been written to the buffer.</p><dl>
<dt><b>STATUS_OBJECT_NAME_NOT_FOUND</b></dt>
</dl><p>The registry value was not available.</p>

<p> </p>

<p>This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>For more information about registry-key objects, see <a href="wdf.using_the_registry_in_kmdf_drivers">Using the Registry in Framework-Based Drivers</a>.</p>

<p>The following code example opens a device's hardware key and retrieves the data that is assigned to the <b>NumberOfToasters</b> value, which is stored under the device's hardware key.</p>

<p>For more information about registry-key objects, see <a href="wdf.using_the_registry_in_kmdf_drivers">Using the Registry in Framework-Based Drivers</a>.</p>

<p>The following code example opens a device's hardware key and retrieves the data that is assigned to the <b>NumberOfToasters</b> value, which is stored under the device's hardware key.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfregistry.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.dll (UMDF)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553410">KEY_VALUE_BASIC_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546804">WdfDeviceOpenRegistryKey</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549920">WdfRegistryQueryMemory</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549921">WdfRegistryQueryMultiString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549923">WdfRegistryQueryString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549925">WdfRegistryQueryULong</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549927">WdfRegistryQueryUnicodeString</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfRegistryQueryValue method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
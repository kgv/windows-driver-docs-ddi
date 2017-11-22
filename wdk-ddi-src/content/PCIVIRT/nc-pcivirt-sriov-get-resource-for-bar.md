---
UID: NC.pcivirt.SRIOV_GET_RESOURCE_FOR_BAR
title: SRIOV_GET_RESOURCE_FOR_BAR
author: windows-driver-content
description: Gets the translated resource for a specific Base Address Register (BAR).
old-location: pci\sriov_get_resource_for_bar.htm
ms.assetid: b52bafee-d541-4396-be0a-06956d07fb2b
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: PCI
req.header: pcivirt.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: *PSRIOV_GET_RESOURCE_FOR_BAR
req.alt-loc: pcivirt.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: PARCLASS_INFORMATION, PARCLASS_INFORMATION, *PPARCLASS_INFORMATION
req.iface: 
---

# SRIOV_GET_RESOURCE_FOR_BAR callback



## -description
<p>Gets the translated resource for a specific Base Address Register (BAR)</p>


## -prototype

````
SRIOV_GET_RESOURCE_FOR_BAR SriovGetResourceForBar;

NTSTATUS SriovGetResourceForBar(
  _In_  PVOID                           Context,
  _In_  USHORT                          VfIndex,
  _In_  USHORT                          BarIndex,
  _Out_ PCM_PARTIAL_RESOURCE_DESCRIPTOR Resource
)
{ ... }

typedef SRIOV_GET_RESOURCE_FOR_BAR *PSRIOV_GET_RESOURCE_FOR_BAR;
````


## -parameters
<dl>

### -param <i>Context</i> [in]

<dd>
<p>A pointer to a driver-defined context.
                    
                </p>
</dd>

### -param <i>VfIndex</i> [in]

<dd>
<p>A zero-based index of the VF that is being queried. </p>
</dd>

### -param <i>BarIndex</i> [in]

<dd>
<p>The index of the BAR (between 0 and 5).</p>
</dd>

### -param <i>Resource</i> [out]

<dd>
<p>
                    
                A pointer to a <a href="https://msdn.microsoft.com/96bf7bab-b8f5-439c-8717-ea6956ed0213">CM_PARTIAL_RESOURCE_DESCRIPTOR</a> structure that is filled with the translated hardware resources for the specified BAR.</p>
</dd>
</dl>

## -returns
<p>
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> error code.</p>

## -remarks
<p>This callback function is implemented by the physical function (PF) driver. It is invoked  when the system wants to access  the translated hardware resources of a particular BAR of a virtual function.</p>

<p>The PF driver registers its implementation by setting the <b>GetResourceForBar</b> member of the SRIOV_DEVICE_INTERFACE_STANDARD, configuring a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552439">WDF_QUERY_INTERFACE_CONFIG</a> structure, and calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545870">WdfDeviceAddQueryInterface</a>.</p>

<p>Here is an example implementation of this callback function. </p>

<p>This callback function is implemented by the physical function (PF) driver. It is invoked  when the system wants to access  the translated hardware resources of a particular BAR of a virtual function.</p>

<p>The PF driver registers its implementation by setting the <b>GetResourceForBar</b> member of the SRIOV_DEVICE_INTERFACE_STANDARD, configuring a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552439">WDF_QUERY_INTERFACE_CONFIG</a> structure, and calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545870">WdfDeviceAddQueryInterface</a>.</p>

<p>Here is an example implementation of this callback function. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Pcivirt.h</dt>
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
</table>
---
UID: NE.ntddk._PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE
title: PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE
author: windows-driver-content
description: The PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE enumeration contains constants that indicate the type of hardware performance counter resource that is described by a PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR structure.
old-location: kernel\physical_counter_resource_descriptor_type.htm
ms.assetid: 58fa1312-eb21-405d-85de-59ea69d9447f
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Supported in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE
req.alt-loc: Ntddk.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: FILTER_INITIALIZATION_DATA, FILTER_INITIALIZATION_DATA, *PFILTER_INITIALIZATION_DATA
req.iface: 
---

# PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE enumeration



## -description
<p>The <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE</b> enumeration contains constants that indicate the type of hardware performance counter resource that is described by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff558796">PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</a> structure.</p>


## -syntax

````
typedef enum _PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE { 
  ResourceTypeSingle                        = 0,
  ResourceTypeRange                         = 1,
  ResourceTypeExtendedCounterConfiguration  = 2,
  ResourceTypeOverflow                      = 3,
  ResourceTypeMax                           = 4
} PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE;
````


## -enum-fields
<dl>

### -field <a id="ResourceTypeSingle"></a><a id="resourcetypesingle"></a><a id="RESOURCETYPESINGLE"></a><b>ResourceTypeSingle</b>

<dd>
<p>A single hardware counter. The counter is described by the <b>u.CounterIndex</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure.</p>
</dd>

### -field <a id="ResourceTypeRange"></a><a id="resourcetyperange"></a><a id="RESOURCETYPERANGE"></a><b>ResourceTypeRange</b>

<dd>
<p>A range of counter indexes. The counter indexes are described by the <b>u.Range</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure.</p>
</dd>

### -field <a id="ResourceTypeExtendedCounterConfiguration"></a><a id="resourcetypeextendedcounterconfiguration"></a><a id="RESOURCETYPEEXTENDEDCOUNTERCONFIGURATION"></a><b>ResourceTypeExtendedCounterConfiguration</b>

<dd>
<p>An extended counter configuration register address. The register address is contained in the <b>u.ExtendedRegisterAddress</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure. This value is used only on Intel NetBurst systems.</p>
</dd>

### -field <a id="ResourceTypeOverflow"></a><a id="resourcetypeoverflow"></a><a id="RESOURCETYPEOVERFLOW"></a><b>ResourceTypeOverflow</b>

<dd>
<p>A counter overflow interrupt. The <b>u</b> member of the <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure is not used for this counter resource type.</p>
</dd>

### -field <a id="ResourceTypeMax"></a><a id="resourcetypemax"></a><a id="RESOURCETYPEMAX"></a><b>ResourceTypeMax</b>

<dd>
<p>The maximum value in this enumeration type. </p>
</dd>
</dl>

## -remarks
<p>The <b>Type</b> member of a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure uses a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE</b> enumeration constant to indicate the type of counter resource that is described by the structure.</p>

<p>The <b>Type</b> member of a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure uses a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE</b> enumeration constant to indicate the type of counter resource that is described by the structure.</p>

<p>The <b>Type</b> member of a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</b> structure uses a <b>PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE</b> enumeration constant to indicate the type of counter resource that is described by the structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h or Ntifs.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558796">PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PHYSICAL_COUNTER_RESOURCE_DESCRIPTOR_TYPE enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
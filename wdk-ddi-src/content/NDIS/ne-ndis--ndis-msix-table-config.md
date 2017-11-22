---
UID: NE.ndis._NDIS_MSIX_TABLE_CONFIG
title: NDIS_MSIX_TABLE_CONFIG
author: windows-driver-content
description: The NDIS_MSIX_TABLE_OPERATION enumeration identifies the type of MSI-X configuration operation.
old-location: netvista\ndis_msix_table_operation.htm
ms.assetid: 7d1a4bb6-5db8-48b0-9be3-7468360951a1
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.1 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_MSIX_TABLE_OPERATION
req.alt-loc: ndis.h
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
ms.keywords: RxNameCacheInitialize
req.iface: 
---

# NDIS_MSIX_TABLE_CONFIG enumeration



## -description
<p>The NDIS_MSIX_TABLE_OPERATION enumeration identifies the type of MSI-X configuration
  operation.</p>


## -syntax

````
typedef enum _NDIS_MSIX_TABLE_CONFIG { 
  NdisMSIXTableConfigSetTableEntry,
  NdisMSIXTableConfigMaskTableEntry,
  NdisMSIXTableConfigUnmaskTableEntry,
  NdisMSIXTableConfigMax
} NDIS_MSIX_TABLE_OPERATION, *PNDIS_MSIX_TABLE_OPERATION;
````


## -enum-fields
<dl>

### -field <a id="NdisMSIXTableConfigSetTableEntry"></a><a id="ndismsixtableconfigsettableentry"></a><a id="NDISMSIXTABLECONFIGSETTABLEENTRY"></a><b>NdisMSIXTableConfigSetTableEntry</b>

<dd>
<p>The MSI-X table entry should be mapped to an MSI-X message that the bus driver allocated to the
     device.</p>
</dd>

### -field <a id="NdisMSIXTableConfigMaskTableEntry"></a><a id="ndismsixtableconfigmasktableentry"></a><a id="NDISMSIXTABLECONFIGMASKTABLEENTRY"></a><b>NdisMSIXTableConfigMaskTableEntry</b>

<dd>
<p>The interrupts from an MSI-X table entry source should be masked.</p>
</dd>

### -field <a id="NdisMSIXTableConfigUnmaskTableEntry"></a><a id="ndismsixtableconfigunmasktableentry"></a><a id="NDISMSIXTABLECONFIGUNMASKTABLEENTRY"></a><b>NdisMSIXTableConfigUnmaskTableEntry</b>

<dd>
<p>The interrupts from an MSI-X table entry source should be unmasked.</p>
</dd>

### -field <a id="NdisMSIXTableConfigMax"></a><a id="ndismsixtableconfigmax"></a><a id="NDISMSIXTABLECONFIGMAX"></a><b>NdisMSIXTableConfigMax</b>

<dd>
<p>The number of enumeration values in NDIS_MSIX_TABLE_OPERATION.</p>
</dd>
</dl>

## -remarks
<p>The NDIS_MSIX_TABLE_OPERATION enumeration is used in the 
    <a href="https://msdn.microsoft.com/52c3238f-4d3a-4241-95bf-630e57e8a6e1">
    NDIS_MSIX_CONFIG_PARAMETERS</a> structure.</p>

<p>The NDIS_MSIX_TABLE_OPERATION enumeration is used in the 
    <a href="https://msdn.microsoft.com/52c3238f-4d3a-4241-95bf-630e57e8a6e1">
    NDIS_MSIX_CONFIG_PARAMETERS</a> structure.</p>

<p>The NDIS_MSIX_TABLE_OPERATION enumeration is used in the 
    <a href="https://msdn.microsoft.com/52c3238f-4d3a-4241-95bf-630e57e8a6e1">
    NDIS_MSIX_CONFIG_PARAMETERS</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.1 and later.</p>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566486">NDIS_MSIX_CONFIG_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_MSIX_TABLE_OPERATION enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
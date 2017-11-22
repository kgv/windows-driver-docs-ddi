---
UID: NS.ndis._NDIS_MSIX_CONFIG_PARAMETERS
title: NDIS_MSIX_CONFIG_PARAMETERS
author: windows-driver-content
description: The NDIS_MSIX_CONFIG_PARAMETERS structure defines a requested configuration operation and specifies the parameters that are required for that particular operation.
old-location: netvista\ndis_msix_config_parameters.htm
ms.assetid: 52c3238f-4d3a-4241-95bf-630e57e8a6e1
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.1 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_MSIX_CONFIG_PARAMETERS
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
req.irql: See Remarks section
ms.keywords: NDIS_MSIX_CONFIG_PARAMETERS, NDIS_MSIX_CONFIG_PARAMETERS, *PNDIS_MSIX_CONFIG_PARAMETERS
req.iface: 
---

# NDIS_MSIX_CONFIG_PARAMETERS structure



## -description
<p>The NDIS_MSIX_CONFIG_PARAMETERS structure defines a requested configuration operation and specifies
  the parameters that are required for that particular operation.</p>


## -syntax

````
typedef struct _NDIS_MSIX_CONFIG_PARAMETERS {
  NDIS_OBJECT_HEADER        Header;
  NDIS_MSIX_TABLE_OPERATION ConfigOperation;
  ULONG                     TableEntry;
  ULONG                     MessageNumber;
} NDIS_MSIX_CONFIG_PARAMETERS, *PNDIS_MSIX_CONFIG_PARAMETERS;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>The 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure for the
     NDIS_MSIX_CONFIG_PARAMETERS structure. The miniport driver sets the 
     <b>Type</b> member of the structure that 
     <b>Header</b> specifies to NDIS_OBJECT_TYPE_DEFAULT, the 
     <b>Revision</b> member to NDIS_MSIX_CONFIG_PARAMETERS_REVISION_1, and the 
     <b>Size</b> member to NDIS_SIZEOF_MSIX_CONFIG_PARAMETERS_REVISION_1.</p>
</dd>

### -field <b>ConfigOperation</b>

<dd>
<p>The requested configuration operation for a MSI-X table entry. This operation is specified as one
     of the values from the 
     <a href="https://msdn.microsoft.com/7d1a4bb6-5db8-48b0-9be3-7468360951a1">
     NDIS_MSIX_TABLE_OPERATION</a> enumeration.</p>
</dd>

### -field <b>TableEntry</b>

<dd>
<p>The MSI-X table entry index.</p>
</dd>

### -field <b>MessageNumber</b>

<dd>
<p>The MSI-X message number that is assigned to the device. This value is required for the 
     <b>NdisMSIXTableConfigSetTableEntry</b> operation. This parameter is not used for the 
     <b>NdisMSIXTableConfigMaskTableEntry</b> or 
     <b>NdisMSIXTableConfigUnmaskTableEntry</b> operations.</p>
</dd>
</dl>

## -remarks
<p>To mask, unmask, or map MSI-X table entries, an NDIS driver passes the NDIS_MSIX_CONFIG_PARAMETERS
    structure to the 
    <a href="https://msdn.microsoft.com/93f94a42-bffb-4e4d-a560-b0da5d7d0019">
    NdisMConfigMSIXTableEntry</a> function. NDIS_MSIX_CONFIG_PARAMETERS defines a requested configuration
    operation and specifies the parameters that are required for that operation.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566489">NDIS_MSIX_TABLE_OPERATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563566">NdisMConfigMSIXTableEntry</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_MSIX_CONFIG_PARAMETERS structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
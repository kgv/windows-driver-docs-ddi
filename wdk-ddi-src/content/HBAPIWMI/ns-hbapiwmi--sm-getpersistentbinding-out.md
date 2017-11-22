---
UID: NS.hbapiwmi._SM_GetPersistentBinding_OUT
title: SM_GetPersistentBinding_OUT
author: windows-driver-content
description: The SM_GetPersistentBinding_OUT structure is used to receive output parameters from the SM_GetPersistentBinding method.
old-location: storage\sm_getpersistentbinding_out.htm
ms.assetid: aa80e05c-e322-4350-80e7-28d53821c510
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: hbapiwmi.h
req.include-header: Hbapiwmi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SM_GetPersistentBinding_OUT
req.alt-loc: hbapiwmi.h
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
ms.keywords: SM_GetPersistentBinding_OUT, SM_GetPersistentBinding_OUT, *PSM_GetPersistentBinding_OUT
req.iface: 
---

# SM_GetPersistentBinding_OUT structure



## -description
<p>The SM_GetPersistentBinding_OUT structure is used to receive output parameters from the SM_GetPersistentBinding method.</p>


## -syntax

````
typedef struct _SM_GetPersistentBinding_OUT {
  ULONG                 HBAStatus;
  ULONG                 TotalEntryCount;
  ULONG                 OutEntryCount;
  MS_SMHBA_BINDINGENTRY Entry[1];
} SM_GetPersistentBinding_OUT, *PSM_GetPersistentBinding_OUT;
````


## -struct-fields
<dl>

### -field <b>HBAStatus</b>

<dd>
<p>The status of the operation. For a list of allowed values and their descriptions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff557233">HBA_STATUS</a>.</p>
</dd>

### -field <b>TotalEntryCount</b>

<dd>
<p>The total number of persistent bindings that are associated with the HBA.</p>
</dd>

### -field <b>OutEntryCount</b>

<dd>
<p>The total number of mappings that are retrieved. This value will be less than or equal to TotalEntryCount.</p>
</dd>

### -field <b>Entry</b>

<dd>
<p>An array of structures of type SMHBA_SCSIENTRY that describes an HBA's bindings between the operating system and the SAS identifiers.</p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite generates a declaration of the SM_GetPersistentBinding_OUT structure in <i>Hbapiwmi.h</i> when it compiles the MS_SM_TargetInformationMethods WMI class.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hbapiwmi.h (include Hbapiwmi.h)</dt>
</dl>
</td>
</tr>
</table>
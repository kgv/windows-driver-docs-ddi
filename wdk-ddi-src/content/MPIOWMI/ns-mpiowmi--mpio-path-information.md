---
UID: NS.mpiowmi._MPIO_PATH_INFORMATION
title: MPIO_PATH_INFORMATION
author: windows-driver-content
description: The MPIO_PATH_INFORMATION structure represents a top-level view of all the paths that are under MPIO control. To query the path information, the request must be sent to the MPIO control object by using its WMI instance name.
old-location: storage\mpio_path_information.htm
ms.assetid: 12383ae0-69c8-4546-9560-08aa4a50de8e
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: mpiowmi.h
req.include-header: Mpiowmi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MPIO_PATH_INFORMATION
req.alt-loc: mpiowmi.h
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
ms.keywords: MPIO_PATH_INFORMATION, MPIO_PATH_INFORMATION, *PMPIO_PATH_INFORMATION
req.iface: 
---

# MPIO_PATH_INFORMATION structure



## -description
<p>The MPIO_PATH_INFORMATION structure represents a top-level view of all the paths that are under MPIO control. To query the path information, the request must be sent to the MPIO control object by using its WMI instance name.</p>


## -syntax

````
typedef struct _MPIO_PATH_INFORMATION {
  ULONG                    NumberPaths;
  ULONG                    Pad;
  MPIO_ADAPTER_INFORMATION PathList[1];
} MPIO_PATH_INFORMATION, *PMPIO_PATH_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>NumberPaths</b>

<dd>
<p>An unsigned 32-bitfield that represents the total number of paths that MPIO is aware of.</p>
</dd>

### -field <b>Pad</b>

<dd>
<p>Should be zero.</p>
</dd>

### -field <b>PathList</b>

<dd>
<p>An array that returns information about each of the paths. The number of elements in the array is given by <i>NumberPaths</i> and each element of the array represents an instance of an MPIO_ADAPTER_INFORMATION structure.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Mpiowmi.h (include Mpiowmi.h)</dt>
</dl>
</td>
</tr>
</table>
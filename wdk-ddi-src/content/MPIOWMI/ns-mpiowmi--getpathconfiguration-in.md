---
UID: NS.mpiowmi._GetPathConfiguration_IN
title: GetPathConfiguration_IN
author: windows-driver-content
description: The GetPathConfiguration_IN structure is used to retrieve the per path device information.
old-location: storage\getpathconfiguration_in.htm
ms.assetid: 38396f75-6bcf-493e-9aab-661db59637ae
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
req.alt-api: GetPathConfiguration_IN
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
ms.keywords: GetPathConfiguration_IN, GetPathConfiguration_IN, *PGetPathConfiguration_IN
req.iface: 
---

# GetPathConfiguration_IN structure



## -description
<p>The GetPathConfiguration_IN structure is used to retrieve the per path device information.</p>


## -syntax

````
typedef struct _GetPathConfiguration_IN {
  ULONGLONG PathID;
} GetPathConfiguration_IN, *PGetPathConfiguration_IN;
````


## -struct-fields
<dl>

### -field <b>PathID</b>

<dd>
<p>A 64-bitfield that specifies the path that is associated with the device.</p>
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
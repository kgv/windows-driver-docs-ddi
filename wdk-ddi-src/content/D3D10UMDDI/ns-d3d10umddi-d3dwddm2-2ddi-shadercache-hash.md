---
UID: NS.d3d10umddi.D3DWDDM2_2DDI_SHADERCACHE_HASH
title: D3DWDDM2_2DDI_SHADERCACHE_HASH
author: windows-driver-content
description: Contains a hash value for a shader cache.
old-location: display\d3dwddm2_2ddi_shadercache_hash.htm
ms.assetid: 1024FF58-7758-473A-8B1F-9CE184B9667A
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DWDDM2_2DDI_SHADERCACHE_HASH
req.alt-loc: d3d10umddi.h
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
ms.keywords: D3DWDDM2_2DDI_SHADERCACHE_HASH, D3DWDDM2_2DDI_SHADERCACHE_HASH
req.iface: 
---

# D3DWDDM2_2DDI_SHADERCACHE_HASH structure



## -description
<p>Contains a hash value for a shader cache.</p>


## -syntax

````
typedef struct D3DWDDM2_2DDI_SHADERCACHE_HASH {
  BYTE Hash[16];
} D3DWDDM2_2DDI_SHADERCACHE_HASH;
````


## -struct-fields
<dl>

### -field <b>Hash</b>

<dd>
<p>A hash value.</p>
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
<dt>D3d10umddi.h</dt>
</dl>
</td>
</tr>
</table>
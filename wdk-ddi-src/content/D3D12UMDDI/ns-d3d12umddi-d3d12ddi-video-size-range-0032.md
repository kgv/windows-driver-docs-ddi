---
UID: NS.d3d12umddi.D3D12DDI_VIDEO_SIZE_RANGE_0032
title: D3D12DDI_VIDEO_SIZE_RANGE_0032
author: windows-driver-content
description: Video size range.
old-location: display\d3d12ddi-video-size-range-0032.htm
ms.assetid: a4781fea-4efc-442d-8503-12be17afa9b1
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d12umddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDI_VIDEO_SIZE_RANGE_0032
req.alt-loc: d3d12umddi.h
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
ms.keywords: D3D12DDI_VIDEO_SIZE_RANGE_0032, D3D12DDI_VIDEO_SIZE_RANGE_0032
req.iface: 
---

# D3D12DDI_VIDEO_SIZE_RANGE_0032 structure



## -description
<p class="CCE_Message">[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]</p>
<p>Video size range.</p>


## -syntax

````
typedef struct _D3D12DDI_VIDEO_SIZE_RANGE_0032 {
  UINT  MaxWidth;
  UINT  MaxHeight;
  UINT  MinWidth;
  UINT  MinHeight;
} D3D12DDI_VIDEO_SIZE_RANGE_0032, D3D12DDI_VIDEO_SIZE_RANGE_0032;
````


## -struct-fields
<dl>

### -field <b>MaxWidth</b>

<dd>
<p>Maximum width.</p>
</dd>

### -field <b>MaxHeight</b>

<dd>
<p>Maximum height.</p>
</dd>

### -field <b>MinWidth</b>

<dd>
<p>Minimum width.</p>
</dd>

### -field <b>MinHeight</b>

<dd>
<p>Minimum height.</p>
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
<dt>D3d12umddi.h</dt>
</dl>
</td>
</tr>
</table>
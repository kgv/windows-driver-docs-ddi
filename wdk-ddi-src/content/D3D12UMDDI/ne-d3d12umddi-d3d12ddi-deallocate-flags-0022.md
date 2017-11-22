---
UID: NE.d3d12umddi.D3D12DDI_DEALLOCATE_FLAGS_0022
title: D3D12DDI_DEALLOCATE_FLAGS_0022
author: windows-driver-content
description: Defines flags for use in deallocation.
old-location: display\d3d12ddi_deallocate_flags_0022.htm
ms.assetid: 17E3C01A-0716-4B3C-B4B3-72B055FB40EA
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3d12umddi.h
req.include-header: D3d12umddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDI_DEALLOCATE_FLAGS_0022
req.alt-loc: D3d12umddi.h
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
ms.keywords: D3DWDDM2_2DDI_SWIZZLE_PATTERN_DESC, D3DWDDM2_2DDI_SWIZZLE_PATTERN_DESC
req.iface: 
---

# D3D12DDI_DEALLOCATE_FLAGS_0022 enumeration



## -description
<p>Defines flags for use in deallocation. </p>


## -syntax

````
typedef enum D3D12DDI_DEALLOCATE_FLAGS_0022 { 
  D3D12DDI_DEALLOCATE_FLAGS_0022_NONE                 = 0x0,
  D3D12DDI_DEALLOCATE_FLAGS_0022_ASSUME_NOT_IN_USE    = 0x1,
  D3D12DDI_DEALLOCATE_FLAGS_0022_SYNCHRONOUS_DESTROY  = 0x2
} D3D12DDI_DEALLOCATE_FLAGS_0022;
````


## -enum-fields
<dl>

### -field <a id="D3D12DDI_DEALLOCATE_FLAGS_0022_NONE"></a><a id="d3d12ddi_deallocate_flags_0022_none"></a><b>D3D12DDI_DEALLOCATE_FLAGS_0022_NONE</b>

<dd>
<p>No flag value.</p>
</dd>

### -field <a id="D3D12DDI_DEALLOCATE_FLAGS_0022_ASSUME_NOT_IN_USE"></a><a id="d3d12ddi_deallocate_flags_0022_assume_not_in_use"></a><b>D3D12DDI_DEALLOCATE_FLAGS_0022_ASSUME_NOT_IN_USE</b>

<dd>
<p>Assume that the allocation is not in use.</p>
</dd>

### -field <a id="D3D12DDI_DEALLOCATE_FLAGS_0022_SYNCHRONOUS_DESTROY"></a><a id="d3d12ddi_deallocate_flags_0022_synchronous_destroy"></a><b>D3D12DDI_DEALLOCATE_FLAGS_0022_SYNCHRONOUS_DESTROY</b>

<dd>
<p>Perform synchronous destroy.</p>
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
<dt>D3d12umddi.h (include D3d12umddi.h)</dt>
</dl>
</td>
</tr>
</table>
---
UID: NS.d3dkmddi._DXGK_ENUM_PIVOT
title: DXGK_ENUM_PIVOT
author: windows-driver-content
description: The DXGK_ENUM_PIVOT structure identifies either a video present source or a video present target as the enumeration pivot in a call to DxgkDdiEnumVidPnCofuncModality.
old-location: display\dxgk_enum_pivot.htm
ms.assetid: f2a234f3-aec9-4fe5-b720-bed9747d5a7f
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_ENUM_PIVOT
req.alt-loc: d3dkmddi.h
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
ms.keywords: DXGK_ENUM_PIVOT, DXGK_ENUM_PIVOT
req.iface: 
---

# DXGK_ENUM_PIVOT structure



## -description
<p>The DXGK_ENUM_PIVOT structure identifies either a video present source or a video present target as the enumeration pivot in a call to <a href="https://msdn.microsoft.com/6dda82bd-1a43-4ffe-b398-a9f8cee6d1c1">DxgkDdiEnumVidPnCofuncModality</a>. </p>


## -syntax

````
typedef struct _DXGK_ENUM_PIVOT {
  D3DDDI_VIDEO_PRESENT_SOURCE_ID VidPnSourceId;
  D3DDDI_VIDEO_PRESENT_TARGET_ID VidPnTargetId;
} DXGK_ENUM_PIVOT;
````


## -struct-fields
<dl>

### -field <b>VidPnSourceId</b>

<dd>
<p>If the pivot of the enumeration is a video present source, this member is the identifier of that source.</p>
</dd>

### -field <b>VidPnTargetId</b>

<dd>
<p>If the pivot of the enumeration is a video present target, this member is the identifier of that target.</p>
</dd>
</dl>

## -remarks
<p>The <b>EnumPivot</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557583">DXGKARG_ENUMVIDPNCOFUNCMODALITY</a> structure is a DXGK_ENUM_PIVOT structure. </p>

<p>The <b>EnumPivotType</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557583">DXGKARG_ENUMVIDPNCOFUNCMODALITY</a> structure is a value from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546003">D3DKMDT_ENUMCOFUNCMODALITY_PIVOT_TYPE</a> enumeration that specifies the pivot type (for example, video present source, video present target, rotation transformation, or scaling transformation).</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>
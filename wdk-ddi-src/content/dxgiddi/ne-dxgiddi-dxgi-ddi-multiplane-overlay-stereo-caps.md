---
UID: NE.dxgiddi.DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS
title: DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS
author: windows-driver-content
description: Reserved for system use. Do not use it in your driver.
old-location: display\dxgi_ddi_multiplane_overlay_stereo_caps.htm
ms.assetid: 28017595-06d5-48ff-91d7-0e084d1e92de
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: dxgiddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS
req.alt-loc: Dxgiddi.h
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
ms.keywords: DxApiGetVersion
req.iface: 
---

# DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS enumeration



## -description
<p>Reserved for system use. Do not use it in your driver.</p>


## -syntax

````
typedef enum DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS { 
  DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_SEPARATE            = 0x1,
  DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_ROW_INTERLEAVED     = 0x4,
  DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_COLUMN_INTERLEAVED  = 0x8,
  DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_CHECKERBOARD        = 0x10,
  DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_FLIP_MODE           = 0x20
} DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS;
````


## -enum-fields
<dl>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_SEPARATE"></a><a id="dxgi_ddi_multiplane_overlay_stereo_caps_separate"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_SEPARATE</b>

<dd></dd>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_ROW_INTERLEAVED"></a><a id="dxgi_ddi_multiplane_overlay_stereo_caps_row_interleaved"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_ROW_INTERLEAVED</b>

<dd></dd>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_COLUMN_INTERLEAVED"></a><a id="dxgi_ddi_multiplane_overlay_stereo_caps_column_interleaved"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_COLUMN_INTERLEAVED</b>

<dd></dd>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_CHECKERBOARD"></a><a id="dxgi_ddi_multiplane_overlay_stereo_caps_checkerboard"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_CHECKERBOARD</b>

<dd></dd>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_FLIP_MODE"></a><a id="dxgi_ddi_multiplane_overlay_stereo_caps_flip_mode"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_STEREO_CAPS_FLIP_MODE</b>

<dd></dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dxgiddi.h</dt>
</dl>
</td>
</tr>
</table>
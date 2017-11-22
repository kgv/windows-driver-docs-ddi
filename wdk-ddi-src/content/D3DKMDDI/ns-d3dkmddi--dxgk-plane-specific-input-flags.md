---
UID: NS.d3dkmddi._DXGK_PLANE_SPECIFIC_INPUT_FLAGS
title: DXGK_PLANE_SPECIFIC_INPUT_FLAGS
author: windows-driver-content
description: A structure containing the input flags to be used for the driver that apply to a plane.
old-location: display\dxgk_plane_specific_input_flags.htm
ms.assetid: 39BE1343-D965-4750-9B94-B54127D873A5
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_PLANE_SPECIFIC_INPUT_FLAGS
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
ms.keywords: DXGK_PLANE_SPECIFIC_INPUT_FLAGS, DXGK_PLANE_SPECIFIC_INPUT_FLAGS
req.iface: 
---

# DXGK_PLANE_SPECIFIC_INPUT_FLAGS structure



## -description
<p>A structure containing the input flags to be used for the driver that apply to a plane.</p>


## -syntax

````
typedef struct _DXGK_PLANE_SPECIFIC_INPUT_FLAGS {
  union {
    struct {
      UINT Enabled  :1;
      UINT FlipImmediate  :1;
      UINT FlipOnNextVSync  :1;
      UINT SharedPrimaryTransition  :1;
      UINT IndependentFlipExclusive  :1;
      UINT Reserved  :27;
    };
    UINT Value;
  };
} DXGK_PLANE_SPECIFIC_INPUT_FLAGS;
````


## -struct-fields
<dl>

### -field <b>Enabled</b>

<dd>
<p>Indicates whether the overlay plane is enabled for display.</p>
</dd>

### -field <b>FlipImmediate</b>

<dd>
<p>Indicates that the driver should perform a flip operation that occurs without vertical sync.</p>
</dd>

### -field <b>FlipOnNextVSync</b>

<dd>
<p>Indicates that the driver should perform a flip operation that occurs on the next vertical sync.</p>
<p>If the current line being displayed is less than DXGK_MULTIPLANE_OVERLAY_PLANE3.MaxImmediateFlipLine, the driver should convert this flip to an immediate flip and set DXGK_PLANE_SPECIFIC_OUTPUT_FLAGS. FlipConvertedToImmediate to TRUE.</p>
</dd>

### -field <b>SharedPrimaryTransition</b>

<dd>
<p>Specifies that the driver is transitioning to or from a shared managed primary allocation.

This member is set if either of the following transitions occurs:
</p>
<ul>
<li>The current primary allocation is not a shared primary allocation, but the new one is.</li>
<li>The current primary allocation is a shared primary allocation, but the new one is not.</li>
</ul>
<p>When SharedPrimaryTransition is set, the display miniport driver must validate that the hardware can seamlessly switch back and forth between primary and shared primary allocations, and it must perform any hardware programming needed to make the seamless switch occur.</p>
</dd>

### -field <b>IndependentFlipExclusive</b>

<dd>
<p>When IndependentFlipExlusive is set, the flip is done in the independent flip exclusive mode. The front buffer is accessed only by the display hardware and not by the DWM. The kernel mode driver can apply vertical sync-related optimizations. </p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member to zero is equivalent to setting the remaining 27 bits (0xFFFFFFE0) of the 32-bit <b>Value</b> member to zeros.</p>
</dd>

### -field <b>Value</b>

<dd></dd>
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
<dt>D3dkmddi.h</dt>
</dl>
</td>
</tr>
</table>
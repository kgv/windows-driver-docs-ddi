---
UID: NS.d3dhal._D3DHAL_DP2PIXELSHADER
title: D3DHAL_DP2PIXELSHADER
author: windows-driver-content
description: DirectX 8.0 and later versions only. The D3DHAL_DP2PIXELSHADER structure is used to set the current pixel shader, or delete a pixel shader, depending on the opcode received (D3DDP2OP_SETPIXELSHADER or D3DDP2OP_DELETEPIXELSHADER) by D3dDrawPrimitives2.
old-location: display\d3dhal_dp2pixelshader.htm
ms.assetid: 820e7667-3adf-49c9-ab44-303f6ea7f4b2
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dhal.h
req.include-header: D3dhal.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DHAL_DP2PIXELSHADER
req.alt-loc: d3dhal.h
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
ms.keywords: D3DHAL_DP2PIXELSHADER, D3DHAL_DP2PIXELSHADER
req.iface: 
---

# D3DHAL_DP2PIXELSHADER structure



## -description
<p>
   DirectX 8.0 and later versions only.
   </p>
<p>The D3DHAL_DP2PIXELSHADER structure is used to set the current pixel shader, or delete a pixel shader, depending on the opcode received (D3DDP2OP_SETPIXELSHADER or D3DDP2OP_DELETEPIXELSHADER) by <a href="https://msdn.microsoft.com/6128ff7a-0d2c-48df-8b5e-cab33c5a74f5">D3dDrawPrimitives2</a>.</p>


## -syntax

````
typedef struct _D3DHAL_DP2PIXELSHADER {
  DWORD dwHandle;
} D3DHAL_DP2PIXELSHADER, *LPD3DHAL_DP2PIXELSHADER;
````


## -struct-fields
<dl>

### -field <b>dwHandle</b>

<dd>
<p>Specifies the handle to the pixel shader that is assigned by the runtime. For delete requests, the handle is guaranteed to be subzero. For set requests, the handle can be zero. If set to zero, the driver should reset any programmable pixel state and revert to fixed function pixel processing behavior (for example, by using render states).</p>
</dd>
</dl>

## -remarks
<p>When switching from fixed function pixel processing to programmable vertex processing the values of, for example, legacy render states and texture stage states should be preserved. If and when a switch from programmable to fixed function pixel processing occurs (the driver receives a D3DDP2OP_SETPIXELSHADER with a shader handle of zero), that preserved state should be restored.</p>

<p>When switching between programmable shaders, any constant register that has a value specified in the definition of that shader should be set to that value. The values of all other constant registers should remain unchanged.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dhal.h (include D3dhal.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/6128ff7a-0d2c-48df-8b5e-cab33c5a74f5">D3dDrawPrimitives2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545752">D3DHAL_DP2SETPIXELSHADERCONST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545467">D3DHAL_DP2CREATEPIXELSHADER</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DHAL_DP2PIXELSHADER structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
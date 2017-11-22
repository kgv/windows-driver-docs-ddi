---
UID: NS.d3dcaps._D3DPrimCaps
title: D3DPrimCaps
author: windows-driver-content
description: Obsolete in DirectX 8.0 and later versions; see Remarks. The D3DPRIMCAPS structure defines the capabilities for each primitive type.
old-location: display\d3dprimcaps.htm
ms.assetid: fa725534-ccc3-4e71-a83f-b25fd4c72c14
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dcaps.h
req.include-header: D3dcaps.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DPRIMCAPS
req.alt-loc: d3dcaps.h
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
ms.keywords: D3DPrimCaps, D3DPRIMCAPS, *LPD3DPRIMCAPS
req.iface: 
---

# D3DPrimCaps structure



## -description
<p>
   Obsolete in DirectX 8.0 and later versions; see Remarks.
   </p>
<p>The D3DPRIMCAPS structure defines the capabilities for each primitive type.</p>


## -syntax

````
typedef struct _D3DPrimCaps {
  DWORD dwSize;
  DWORD dwMiscCaps;
  DWORD dwRasterCaps;
  DWORD dwZCmpCaps;
  DWORD dwSrcBlendCaps;
  DWORD dwDestBlendCaps;
  DWORD dwAlphaCmpCaps;
  DWORD dwShadeCaps;
  DWORD dwTextureCaps;
  DWORD dwTextureFilterCaps;
  DWORD dwTextureBlendCaps;
  DWORD dwTextureAddressCaps;
  DWORD dwStippleWidth;
  DWORD dwStippleHeight;
} D3DPRIMCAPS, *LPD3DPRIMCAPS;
````


## -struct-fields
<dl>

### -field <b>dwSize</b>

<dd>
<p>Specifies the size, in bytes, of the D3DPRIMCAPS structure. </p>
</dd>

### -field <b>dwMiscCaps</b>

<dd>
<p>Specifies the general capabilities for this primitive. This member can be one or more of the following:    
  
</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPMISCCAPS_CONFORMANT</td>
<td>The device conforms to the OpenGL standard. 
  </td>
</tr>
<tr>
<td>D3DPMISCCAPS_CULLCCW</td>
<td>The driver supports counterclockwise culling through the D3DRENDERSTATE_CULLMODE render state. (This applies only to triangle primitives.) This corresponds to the D3DCULL_CCW enumerator of the D3DCULL enumerated type. 
</td>
</tr>
<tr>
<td>D3DPMISCCAPS_CULLCW</td>
<td>The driver supports clockwise triangle culling through the D3DRENDERSTATE_CULLMODE render state. (This applies only to triangle primitives.) This corresponds to the D3DCULL_CW enumerator of the D3DCULL enumerated type. 
</td>
</tr>
<tr>
<td>D3DPMISCCAPS_CULLNONE</td>
<td>The driver does not perform triangle culling. This corresponds to the D3DCULL_NONE enumerator of the D3DCULL enumerated type.</td>
</tr>
<tr>
<td>D3DPMISCCAPS_LINEPATTERNREP </td>
<td>
<p>The driver can handle values other than 1 in the <b>wRepeatFactor</b> member of the D3DLINEPATTERN structure. (This applies only to line-drawing primitives.)

</p>
<p>Applications can set the line-pattern-repetition number to a maximum value of 65535 (16-bit value). However, hardware only supports a maximum of 255 (8-bit value). Therefore, a display driver must fail a request that attempts to set this number to a value greater than 255 as an invalid request. For more information, see <a href="https://msdn.microsoft.com/090b823a-59d0-40e1-8feb-0b03b7f08fee">Setting the Number of Line Pattern Repetitions</a>.

</p>
<p>D3DPMISCCAPS_LINEPATTERNREP and D3DPRASTERCAPS_PAT must be set consistently (both on or both off).

 
</p>
</td>
</tr>
<tr>
<td>D3DPMISCCAPS_MASKPLANES</td>
<td>The device can perform a bitmask of color planes.</td>
</tr>
<tr>
<td>D3DPMISCCAPS_MASKZ</td>
<td>The device can enable and disable modification of the z-buffer on pixel operations.</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwRasterCaps</b>

<dd>
<p>Contains information about raster-drawing capabilities. This member can be one or more of the following:</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPRASTERCAPS_ANISOTROPY</td>
<td>The device supports anisotropic filtering. For more information, see D3DTSS_MAXANISOTROPY in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ANTIALIASEDGES</td>
<td>The device can antialias lines forming the convex outline of objects. For more information, see D3DRENDERSTATE_EDGEANTIALIAS in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ANTIALIASSORTDEPENDENT</td>
<td>The device supports antialiasing that is dependent on the sort order of the polygons (back-to-front or front-to-back). The application must draw polygons in the right order for antialiasing to occur. For more information, see the D3DANTIALIASMODE enumerated type in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ANTIALIASSORTINDEPENDENT</td>
<td>The device supports antialiasing that is not dependent on the sort order of the polygons. For more information, see the D3DANTIALIASMODE enumerated type in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_DITHER</td>
<td>The device can dither to improve color resolution through the D3DRENDERSTATE_DITHERENABLE render state.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_FOGRANGE</td>
<td>The device supports range-based fog, in which the distance of an object from the viewer, rather than the depth of the object (its z-coordinate), is used to compute fog effects in the scene. For more information, see D3DRENDERSTATE_RANGEFOGENABLE in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_FOGTABLE</td>
<td>The device calculates the fog value by referring to a look-up table containing fog values that are indexed to the depth of a given pixel. For more information, see D3DRENDERSTATE_FOGCOLOR, D3DRENDERSTATE_FOGDENSITY, D3DRENDERSTATE_FOGENABLE, D3DRENDERSTATE_FOGEND, D3DRENDERSTATE_FOGSTART, and D3DRENDERSTATE_FOGTABLEMODE in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_FOGVERTEX</td>
<td>The device calculates the fog value during the lighting operation, places the value into the alpha component of the D3DCOLOR value given for the specular member of the D3DTLVERTEX structure (defined in the Direct3D SDK documentation), and interpolates the fog value during rasterization. For more information, see D3DRENDERSTATE_FOGCOLOR, D3DRENDERSTATE_FOGDENSITY, D3DRENDERSTATE_FOGENABLE, D3DRENDERSTATE_FOGEND, D3DRENDERSTATE_FOGSTART, and D3DRENDERSTATE_FOGVERTEXMODE in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_PAT</td>
<td>
<p>The driver can perform patterned drawing (lines or fills with D3DRENDERSTATE_LINEPATTERN or one of the D3DRENDERSTATE_STIPPLEPATTERN render states) for the primitive being queried.

</p>
<p>D3DPRASTERCAPS_PAT and D3DPMISCCAPS_LINEPATTERNREP must be set consistently (both on or both off).</p>
</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ROP2</td>
<td>The device can support raster operations other than R2_COPYPEN.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_STIPPLE</td>
<td>The device can stipple polygons to simulate translucency.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_SUBPIXEL</td>
<td>The device performs subpixel placement of z, color, and texture data, rather than working with the nearest-integer pixel coordinate. This helps avoid bleedthrough due to z imprecision, and jitter of color and texture values for pixels. Note that there is no corresponding state that can be enabled and disabled; the device either performs subpixel placement or it does not, and this bit is present only so that the Direct3D client can better determine what the rendering quality is.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_SUBPIXELX</td>
<td>The device is subpixel-accurate along the x-axis only, and is clamped to an integer y-axis scan line. For information about subpixel accuracy, see the previously mentioned definition of D3DPRASTERCAPS_SUBPIXEL.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_TRANSLUCENTSORTINDEPENDENT</td>
<td>The hardware can perform translucency without sorting. This is an offshoot of the A buffer technique for antialiasing.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_WBUFFER</td>
<td>The device supports w-buffering.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_WFOG</td>
<td>The device supports w-based fog.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_XOR</td>
<td>The device can support XOR operations. If this flag is not set but D3DPRASTER_ROP2 is set, then XOR operations must still be supported.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ZBIAS</td>
<td>The device supports z-bias values, integer values assigned to polygons to allow physically coplanar polygons to appear separate. For more information, see D3DRENDERSTATE_ZBIAS in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ZBUFFERLESSHSR</td>
<td>The device can perform hidden-surface removal (HSR) without requiring the application to sort polygons, and without requiring the allocation of a z-buffer. This leaves more video memory for textures. The method used to perform HSR is hardware-dependent and is transparent to the application. Z-buffer-less HSR is performed if no z-buffer surface is attached to the rendering target surface and the z-buffer comparison test is enabled (that is, when the state value associated with the D3DRENDERSTATE_ZENABLE render state value is set to <b>TRUE</b>).</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ZFOG</td>
<td>The device supports z based fog.</td>
</tr>
<tr>
<td>D3DPRASTERCAPS_ZTEST</td>
<td>The device can perform z-test operations. This effectively renders a primitive and indicates whether any z pixels would have been rendered.</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwZCmpCaps</b>

<dd>
<p>Specifies Z-buffer comparison functions that the driver can perform through the D3DRENDERSTATE_ZFUNC render state. This member can be one or more of the following:  
  
 
 
</p>
<table>
<tr>
<th>Comparison Function</th>
<th>Description</th>
</tr>
<tr>
<td>D3DPCMPCAPS_ALWAYS   
   
 </td>
<td>Always pass the z test. 
</td>
</tr>
<tr>
<td>D3DPCMPCAPS_EQUAL</td>
<td>Pass the z test if the new z equals the current z.</td>
</tr>
<tr>
<td>D3DPCMPCAPS_GREATER</td>
<td>Pass the z test if the new z is greater than the current z.</td>
</tr>
<tr>
<td>D3DPCMPCAPS_GREATEREQUAL</td>
<td>Pass the z test if the new z is greater than or equal to the current z.</td>
</tr>
<tr>
<td>D3DPCMPCAPS_LESS</td>
<td>Pass the z test if the new z is less than the current z.</td>
</tr>
<tr>
<td>D3DPCMPCAPS_LESSEQUAL </td>
<td>Pass the z test if the new z is less than or equal to the current z. 
</td>
</tr>
<tr>
<td>D3DPCMPCAPS_NEVER </td>
<td>Always fail the z test.</td>
</tr>
<tr>
<td>D3DPCMPCAPS_NOTEQUAL </td>
<td>Pass the z test if the new z does not equal the current z.</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwSrcBlendCaps</b>

<dd>
<p>Specifies source blending capabilities supported by the driver through the D3DRENDERSTATE_SRCBLEND render state. This member can be one or more of the following values. (The RGBA values of the source and destination are indicated with the subscripts s and d.)  
  
</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPBLENDCAPS_BOTHINVSRCALPHA </td>
<td>Source blend factor is (1 - Aₛ, 1 - Aₛ, 1 - Aₛ, 1 - Aₛ) and destination blend factor is (As, As, As, As); the destination blend selection is overridden. 
</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_BOTHSRCALPHA</td>
<td>Source blend factor is (Aₛ, Aₛ, Aₛ, Aₛ) and destination blend factor is (1 - Aₛ, 1 - Aₛ, 1 - Aₛ, 1 - Aₛ); the destination blend selection is overridden.</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_DESTALPHA</td>
<td>Blend factor is (A<sub>d</sub>, A<sub>d</sub>, A<sub>d</sub>, A<sub>d</sub>).</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_DESTCOLOR</td>
<td>Blend factor is (R<sub>d</sub>, G<sub>d</sub>, B<sub>d</sub>, A<sub>d</sub>).</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_INVDESTALPHA</td>
<td>Blend factor is (1 - A<sub>d</sub>, 1 - A<sub>d</sub>, 1 - A<sub>d</sub>, 1 - A<sub>d</sub>).</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_INVDESTCOLOR</td>
<td>Blend factor is (1 - R<sub>d</sub>, 1 - G<sub>d</sub>, 1 - B<sub>d</sub>, 1 - A<sub>d</sub>).</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_INVSRCALPHA</td>
<td>Blend factor is (1 - Aₛ, 1 - Aₛ, 1 - Aₛ, 1 - Aₛ). 
 </td>
</tr>
<tr>
<td>D3DPBLENDCAPS_INVSRCCOLOR</td>
<td>Blend factor is (1 - Rₛ, 1 - Gₛ, 1 - Bₛ, 1 - Aₛ).</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_ONE</td>
<td>Blend factor is (1, 1, 1, 1). 
 </td>
</tr>
<tr>
<td>D3DPBLENDCAPS_SRCALPHA</td>
<td>Blend factor is (Aₛ, Aₛ, Aₛ, Aₛ). 
 </td>
</tr>
<tr>
<td>D3DPBLENDCAPS_SRCALPHASAT </td>
<td>Blend factor is (f, f, f, 1); f = min(Aₛ, 1 - A<sub>d</sub>). 
 
</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_SRCCOLOR </td>
<td>Blend factor is (Rₛ, Gₛ, Bₛ, Aₛ).</td>
</tr>
<tr>
<td>D3DPBLENDCAPS_ZERO</td>
<td>Blend factor is (0, 0, 0, 0). 
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwDestBlendCaps</b>

<dd>
<p>Specifies destination blending capabilities supported by the driver through the D3DRENDERSTATE_DESTBLEND render state. This member can be the same capabilities that are defined for the <b>dwSrcBlendCaps</b> member. </p>
</dd>

### -field <b>dwAlphaCmpCaps</b>

<dd>
<p>Specifies alpha-test comparison functions that the driver can perform. This member uses the same comparison functions as are defined for the <b>dwZCmpCaps</b> member. If the <b>dwAlphaCmpCaps</b> member of the D3DPRIMCAPS structure is 0, the driver does not support alpha test render states D3DRENDERSTATE_ALPHAFUNC, D3DRENDERSTATE_ALPHAREF, and D3DRENDERSTATE_ALPHATESTENABLE. </p>
</dd>

### -field <b>dwShadeCaps</b>

<dd>
<p>Specifies shading operations that the device can perform. It is assumed, in general, that if a device supports a given command (such as D3DOP_TRIANGLE) at all, it supports the D3DSHADE_FLAT mode (as specified in the D3DSHADEMODE enumerated type in the DirectX SDK documentation). This flag specifies whether the driver can also support Gouraud and Phong shading and whether alpha color components are supported for each of the three color-generation modes. When alpha components are not supported in a given mode, the alpha value of colors generated in that mode is implicitly 255. This is the maximum possible alpha (that is, the alpha component is at full intensity).</p>
<p> 
The color, specular highlights, fog, and alpha interpolants of a triangle each have capability flags that an application can use to find out how they are implemented by the device driver. These are modified by the shade mode and color model, and by whether the alpha component of a color is blended or stippled.</p>
<p>This member can be one or more of values listed in the following table. Related flags are grouped together in this table.</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPSHADECAPS_ALPHAFLATBLEND
D3DPSHADECAPS_ALPHAFLATSTIPPLED</td>
<td>The device can support an alpha component for flat-blended and stippled (D3DRENDERSTATE_STIPPLEDALPHA) transparency, respectively (the D3DSHADE_FLAT state for the D3DSHADEMODE enumerated type). In these modes, the alpha color component for a primitive is provided as part of the color for the first vertex of the primitive.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_ALPHAGOURAUDBLEND
D3DPSHADECAPS_ALPHAGOURAUDSTIPPLED</td>
<td>The device can support an alpha component for Gouraud blended and stippled (D3DRENDERSTATE_STIPPLEDALPHA) transparency, respectively (the D3DSHADE_GOURAUD state for the D3DSHADEMODE enumerated type). In these modes, the alpha color component for a primitive is provided at vertices and interpolated across a face along with the other color components.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_ALPHAPHONGBLEND
D3DPSHADECAPS_ALPHAPHONGSTIPPLED</td>
<td>The device can support an alpha component for Phong-blended and stippled (D3DRENDERSTATE_STIPPLEDALPHA) transparency, respectively (the D3DSHADE_PHONG state for the D3DSHADEMODE enumerated type). In these modes, vertex parameters are reevaluated on a per-pixel basis, applying lighting effects for the red, green, and blue color components.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_COLORFLATMONO
D3DPSHADECAPS_COLORFLATRGB</td>
<td>The device can support colored flat shading in the D3DCOLOR_MONO and D3DCOLOR_RGB color models, respectively. In these modes, the color component for a primitive is provided as part of the color for the first vertex of the primitive. In monochromatic lighting modes, only the blue component of the color is interpolated; in RGB lighting modes, of course, the red, green, and blue components are interpolated.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_COLORGOURAUDMONO
D3DPSHADECAPS_COLORGOURAUDRGB</td>
<td>The device can support colored Gouraud shading in the D3DCOLOR_MONO and D3DCOLOR_RGB color models, respectively. In these modes, the color component for a primitive is provided at vertices and interpolated across a face along with the other color components. In monochromatic lighting modes, only the blue component of the color is interpolated; in RGB lighting modes, of course, the red, green, and blue components are interpolated.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_COLORPHONGMONO
D3DPSHADECAPS_COLORPHONGRGB</td>
<td>The device can support colored Phong shading in the D3DCOLOR_MONO and D3DCOLOR_RGB color models, respectively. In these modes, vertex parameters are reevaluated on a per-pixel basis. Lighting effects are applied for the red, green, and blue color components in RGB mode, and for the blue component only for monochromatic mode.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_FOGFLAT
D3DPSHADECAPS_FOGGOURAUD,
D3DPSHADECAPS_FOGPHONG</td>
<td>The device can support fog in the flat, Gouraud, and Phong shading models, respectively.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_SPECULARFLATMONO
D3DPSHADECAPS_SPECULARFLATRGB</td>
<td>The device can support specular highlights through the D3DRENDERSTATE_SPECULARENABLE render state in flat shading in the D3DCOLOR_MONO and D3DCOLOR_RGB color models, respectively.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_SPECULARGOURAUDMONO
D3DPSHADECAPS_SPECULARGOURAUDRGB</td>
<td>The device can support specular highlights through the D3DRENDERSTATE_SPECULARENABLE render state in Gouraud shading in the D3DCOLOR_MONO and D3DCOLOR_RGB color models, respectively.</td>
</tr>
<tr>
<td>D3DPSHADECAPS_SPECULARPHONGMONO
D3DPSHADECAPS_SPECULARPHONGRGB</td>
<td>The device can support specular highlights through the D3DRENDERSTATE_SPECULARENABLE render state in Phong shading in the D3DCOLOR_MONO and D3DCOLOR_RGB color models, respectively. Phong shading is not supported for DirectX 2.0.</td>
</tr>
</table>
<p> </p>
<p>Most hardware drivers should expose the D3DPSHADECAPS_COLORFLATRGB and D3DPSHADECAPS_COLORGOURAUDRGB capabilities. Hardware that supports intensity (grayscale) lighting (see D3DRENDERSTATE_MONOENABLE for more details) should also expose the D3DPSHADECAPS_COLORFLATMONO and D3DSHADECAPS_COLORGOURAUDMONO capabilities.</p>
</dd>

### -field <b>dwTextureCaps</b>

<dd>
<p>Specifies miscellaneous texture-mapping capabilities. This member can be one or more of the following: </p>
<table>
<tr>
<th>Value</th>
<th>Meaining</th>
</tr>
<tr>
<td>D3DPTEXTURECAPS_ALPHA</td>
<td>RGBA textures are supported in the D3DTEX_DECAL and D3DTEX_MODULATE texture filtering modes. If this capability is not set, then only RGB textures are supported in those modes. Regardless of whether this flag is set, alpha must always be supported in the D3DTEX_DECAL_MASK, D3DTEX_DECAL_ALPHA, and D3DTEX_MODULATE_ALPHA filtering modes whenever those filtering modes are available.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_ALPHAPALETTE</td>
<td>Palletized texture surfaces whose palettes contain alpha information are supported (see the DDPCAPS_ALPHA flag in the DDCAPS structure in the DirectDraw SDK documentation).</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_BORDER</td>
<td>Texture mapping along borders is supported.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_COLORKEYBLEND</td>
<td>The device is capable of performing color key blending.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_CUBEMAP</td>
<td>The device is capable of supporting cube environment mapping.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_PERSPECTIVE</td>
<td>Perspective correction is supported. See D3DRENDERSTATE_TEXTUREPERSPECTIVE in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_POW2</td>
<td>Under typical conditions, the device requires that textures have widths and heights specified as powers of 2. This requirement does not apply to either cube textures or volume textures. If this flag is set, the D3DPTEXTURECAPS_NONPOW2CONDITIONAL flag might also be set.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_PROJECTED</td>
<td>The device can divide transformed texture coordinates by the COUNTth texture coordinate. In other words, the device can do D3DTTFF_PROJECTED. See D3DTEXTURETRANSFORMFLAGS in the DirectX SDK documentation.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_NONPOW2CONDITIONAL</td>
<td>
<p>Conditionally supports the use of two-dimensional (2D) textures (that is, not volume or cube textures) with dimensions that are not powers of 2. A device that exposes this capability can use such a texture if all of the following requirements are met. </p>
<ul>
<li>The texture addressing mode for the texture stage is set to D3DTADDRESS_CLAMP. </li>
<li>Texture wrapping for the texture stage is disabled (D3DRS_WRAPn set to 0). </li>
<li>Mipmapping is not in use (use magnification filter only). </li>
<li>Texture was not stored in DXT1-5 (compressed texture formats). </li>
</ul>
<p>A driver for a device that exposes this capability cannot perform dependent texture reads using such a texture. That is, such a texture cannot be addressed or sampled using texture coordinates that are computed with <a href="https://msdn.microsoft.com/ddf3c7b2-93fe-412e-b52b-632402327cb8">shader code</a>. In other words, such a texture cannot be set at a stage that will be read based on a shader computation such as the bem, beml, or texm3x3 instructions in versions 1.0-1.3 of pixel shaders. For example, these textures can be used to store bump-map data that the driver supplies to texture reads, but not the environment maps that are used in texbem, texbeml, or texm3x3spec.</p>
<p>If this flag is set, the D3DPTEXTURECAPS_POW2 flag must also be set.</p>
</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_SQUAREONLY</td>
<td>All textures must be square.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_TEXREPEATNOTSCALESBYSIZE</td>
<td>Texture indexes are not scaled by the texture size before interpolation.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_TEXTURETRANSFORM</td>
<td>The device is capable of doing texture transforms.</td>
</tr>
<tr>
<td>D3DPTEXTURECAPS_TRANSPARENCY</td>
<td>Texture transparency is supported. (Only those texels that are not the current transparent color are drawn.)</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwTextureFilterCaps</b>

<dd>
<p>Specifies texture-mapping capabilities. This member can be one or more of the following: 
  
  
 </p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPTFILTERCAPS_LINEAR</td>
<td>Bilinear filtering is supported. A weighted average of a 2-by-2 area of texels surrounding the desired pixel is used. This applies to both zooming in and zooming out. If either zooming in or zooming out is supported, then both must be supported.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_LINEARMIPLINEAR</td>
<td>Trilinear interpolation between MIP maps is supported. Performs bilinear filtering on the two nearest MIP maps, then interpolates linearly between the two colors to determine the final color.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_LINEARMIPNEAREST</td>
<td>Linear interpolation between two point sampled MIP maps is supported. Chooses the nearest texel from the two closest MIP map levels, then performs linear interpolation between them. 
</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MAGFAFLATCUBIC</td>
<td>Per-stage flat-cubic filtering for magnifying textures is supported. The flat-cubic magnification filter is represented by the D3DTFG_FLATCUBIC member of the D3DTEXTUREMAGFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MAGFANISOTROPIC</td>
<td>Per-stage anisotropic filtering for magnifying textures is supported. The anisotropic magnification filter is represented by the D3DTFG_ANISOTROPIC member of the D3DTEXTUREMAGFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MAGFGAUSSIANCUBIC</td>
<td>Per-stage Gaussian-cubic filtering for magnifying textures is supported. The Gaussian-cubic magnification filter is represented by the D3DTFG_GAUSSIANCUBIC member of the D3DTEXTUREMAGFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MAGFLINEAR</td>
<td>Per-stage bilinear-interpolation filtering for magnifying textures is supported. The bilinear-interpolation magnification filter is represented by the D3DTFG_LINEAR member of the D3DTEXTUREMAGFILTER enumeration.
Specifies that bilinear filtering on the magnify filter is supported.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MAGFPOINT</td>
<td>Per-stage point-sampled filtering for magnifying textures is supported. The point-sample magnification filter is represented by the D3DTFG_POINT member of the D3DTEXTUREMAGFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MINFANISOTROPIC</td>
<td>Per-stage anisotropic filtering for minifying textures is supported. The anisotropic minification filter is represented by the D3DTFN_ANISOTROPIC member of the D3DTEXTUREMINFILTER enumeration. 
</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MINFLINEAR</td>
<td>Per-stage bilinear-interpolation filtering for minifying textures is supported. The bilinear minification filter is represented by the D3DTFN_LINEAR member of the D3DTEXTUREMINFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MINFPOINT</td>
<td>Per-stage point-sampled filtering for minifying textures is supported. The point-sample minification filter is represented by the D3DTFN_POINT member of the D3DTEXTUREMINFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MIPFLINEAR</td>
<td>Per-stage trilinear-interpolation filtering for MIP maps (that is, bilinear filtering between MIP levels) is supported. The trilinear-interpolation MIP mapping filter is represented by the D3DTFP_LINEAR member of the D3DTEXTUREMIPFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MIPFPOINT</td>
<td>Per-stage point-sampled filtering for MIP maps is supported. The point-sample MIP mapping filter is represented by the D3DTFP_POINT member of the D3DTEXTUREMIPFILTER enumeration.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MIPLINEAR</td>
<td>Nearest MIP mapping, with bilinear filtering applied to the result is supported. Chooses the texel from the appropriate MIP map that has the nearest coordinates, then performs a weighted average with the four surrounding texels to determine the final color.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_MIPNEAREST</td>
<td>Nearest MIP mapping is supported. Chooses the texel from the appropriate MIP map with coordinates nearest to the desired pixel value.</td>
</tr>
<tr>
<td>D3DPTFILTERCAPS_NEAREST</td>
<td>Point sampling is supported. The texel with coordinates nearest to the desired pixel value is used. This applies to both zooming in and zooming out. If either zooming in or zooming out is supported, then both must be supported. 
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwTextureBlendCaps</b>

<dd>
<p>Specifies texture-blending capabilities. See the D3DRENDERSTATE_TEXTUREMAPBLEND enumerated type for discussions of the various texture-blending modes. This member can be one or more of the following:   
  
 </p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPTBLENDCAPS_ADD</td>
<td>Add mode texture-blending is supported (D3DTBLEND_COPY from the D3DTEXTUREBLEND enumerated type).</td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_COPY</td>
<td>Copy mode texture-blending is supported (D3DTBLEND_COPY from the D3DTEXTUREBLEND enumerated type). 
</td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_DECAL</td>
<td> Decal texture-blending mode is supported (D3DTBLEND_DECAL from the D3DTEXTUREBLEND enumerated type).</td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_DECALALPHA</td>
<td>Decal-alpha texture-blending mode is supported (D3DTBLEND_DECALALPHA from the D3DTEXTUREBLEND enumerated type). 
 </td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_DECALMASK</td>
<td>Decal-mask texture-blending mode is supported (D3DTBLEND_DECALMASK from the D3DTEXTUREBLEND enumerated type).</td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_MODULATE</td>
<td>Modulate-texture-blending mode is supported (D3DTBLEND_MODULATE from the D3DTEXTUREBLEND enumerated type).</td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_MODULATEALPHA</td>
<td>Modulate-alpha texture-blending mode is supported (D3DTBLEND_MODULATEALPHA from the D3DTEXTUREBLEND enumerated type).</td>
</tr>
<tr>
<td>D3DPTBLENDCAPS_MODULATEMASK</td>
<td>Modulate-mask texture-blending mode is supported (D3DTBLEND_MODULATEMASK from the D3DTEXTUREBLEND enumerated type). 
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwTextureAddressCaps</b>

<dd>
<p>Specifies the texture-addressing capabilities. This member can be one or more of the following, corresponding to D3DTEXTUREADDRESS texture-addressing modes:</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>D3DPTADDRESSCAPS_BORDER</td>
<td>The device supports setting coordinates outside the range [0.0, 1.0] to the border color, as specified by the D3DTSS_BORDERCOLOR texture stage state. This ability corresponds to the D3DTADDRESS_BORDER texture-addressing mode. 
 </td>
</tr>
<tr>
<td>D3DPTADDRESSCAPS_CLAMP</td>
<td>The device can clamp textures to addresses. This ability corresponds to the D3DTADDRESS_CLAMP texture-addressing mode.</td>
</tr>
<tr>
<td>D3DPTADDRESSCAPS_INDEPENDENTUV</td>
<td>The device can separate the texture-addressing modes of the U and V coordinates of the texture. This ability corresponds to the D3DTSS_ADDRESSU and D3DTSS_ADDRESSV texture stage states. 
</td>
</tr>
<tr>
<td>D3DPTADDRESSCAPS_MIRROR</td>
<td>The device can mirror textures to addresses. This ability corresponds to the D3DTADDRESS_MIRROR texture-addressing mode.</td>
</tr>
<tr>
<td>D3DPTADDRESSCAPS_WRAP</td>
<td>The device can wrap textures to addresses. This ability corresponds to the D3DTADDRESS_WRAP texture-addressing mode.</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>dwStippleWidth</b>

<dd></dd>

### -field <b>dwStippleHeight</b>

<dd>
<p>Specify the maximum width and height of the supported stipple (up to 32-by-32). </p>
</dd>
</dl>

## -remarks
<p>This structure has been replaced by D3DCAPS8 (see the DirectX 8.0 SDK documentation) for DirectX 8.0 and later runtimes, but is required for DirectX 7.0 and earlier runtime compatibility. See <a href="https://msdn.microsoft.com/a03a7cbc-95be-4251-8e3a-bef4a093f03d">Reporting DirectX 8.0 Style Direct3D Capabilities</a> for details.</p>

<p>This structure is used when a device is created and when the capabilities of a device are queried. It defines several members in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544689">D3DDEVICEDESC_V1</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dcaps.h (include D3dcaps.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544689">D3DDEVICEDESC_V1</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DPRIMCAPS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NC.d3dumddi.PFND3DDDI_SETTEXTURE
title: PFND3DDDI_SETTEXTURE
author: windows-driver-content
description: The SetTexture function inserts a texture at a particular stage in a multiple-texture group.
old-location: display\settexture.htm
ms.assetid: b2ed86c5-cd4f-4aaa-a062-4c7ae4e088df
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SetTexture
req.alt-loc: d3dumddi.h
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
ms.keywords: DXGK_MIRACAST_CHUNK_INFO, DXGK_MIRACAST_CHUNK_INFO
req.iface: 
---

# PFND3DDDI_SETTEXTURE callback



## -description
<p>The <i>SetTexture</i> function inserts a texture at a particular stage in a multiple-texture group.</p>


## -prototype

````
PFND3DDDI_SETTEXTURE SetTexture;

__checkReturn HRESULT APIENTRY SetTexture(
  _In_ HANDLE hDevice,
  _In_ UINT   Stage,
  _In_ HANDLE hTexture
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to the display device (graphics context).</p>
</dd>

### -param <i>Stage</i> [in]

<dd>
<p> The stage in a multiple-texture group that indicates where to insert the texture that is specified by the <i>hTexture</i> handle. This parameter can be an integer in the range from 0 through 7, with the highest-numbered texture being closest to the frame buffer.</p>
</dd>

### -param <i>hTexture</i> [in]

<dd>
<p> A handle to the texture to insert.</p>
</dd>
</dl>

## -returns
<p><i>SetTexture</i> returns S_OK or an appropriate error result if the texture is not successfully inserted.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544519">D3DDDI_DEVICEFUNCS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_SETTEXTURE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
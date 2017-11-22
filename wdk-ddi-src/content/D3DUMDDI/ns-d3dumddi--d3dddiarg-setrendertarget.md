---
UID: NS.d3dumddi._D3DDDIARG_SETRENDERTARGET
title: D3DDDIARG_SETRENDERTARGET
author: windows-driver-content
description: The D3DDDIARG_SETRENDERTARGET structure describes the render target surface.
old-location: display\d3dddiarg_setrendertarget.htm
ms.assetid: 88b0de48-1b85-4733-809c-6d8da657e920
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDIARG_SETRENDERTARGET
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
ms.keywords: D3DDDIARG_SETRENDERTARGET, D3DDDIARG_SETRENDERTARGET
req.iface: 
---

# D3DDDIARG_SETRENDERTARGET structure



## -description
<p>The D3DDDIARG_SETRENDERTARGET structure describes the render target surface. </p>


## -syntax

````
typedef struct _D3DDDIARG_SETRENDERTARGET {
  UINT   RenderTargetIndex;
  HANDLE hRenderTarget;
  UINT   SubResourceIndex;
} D3DDDIARG_SETRENDERTARGET;
````


## -struct-fields
<dl>

### -field <b>RenderTargetIndex</b>

<dd>
<p>[in] An index into the group of render target surfaces.</p>
</dd>

### -field <b>hRenderTarget</b>

<dd>
<p>[in] A handle to the render target surface or the group of render target surfaces.</p>
</dd>

### -field <b>SubResourceIndex</b>

<dd>
<p>[in] An index into the resource for the render target.</p>
</dd>
</dl>

## -remarks


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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/067378bd-a2d8-4c83-9436-531519eadaa3">SetRenderTarget</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDIARG_SETRENDERTARGET structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NC.d3d10umddi.PFND3D10DDI_RESOURCERESOLVESUBRESOURCE
title: PFND3D10DDI_RESOURCERESOLVESUBRESOURCE
author: windows-driver-content
description: The ResourceResolveSubresource function resolves multiple samples to one pixel.
old-location: display\resourceresolvesubresource.htm
ms.assetid: f9f4a6e2-bc01-477f-a919-ec71871f665b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ResourceResolveSubresource
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
ms.keywords: SETRESULT_INFO, SETRESULT_INFO, *PSETRESULT_INFO
req.iface: 
---

# PFND3D10DDI_RESOURCERESOLVESUBRESOURCE callback



## -description
<p>The <i>ResourceResolveSubresource</i> function resolves multiple samples to one pixel.</p>


## -prototype

````
PFND3D10DDI_RESOURCERESOLVESUBRESOURCE ResourceResolveSubresource;

VOID APIENTRY ResourceResolveSubresource(
  _In_ D3D10DDI_HDEVICE   hDevice,
  _In_ D3D10DDI_HRESOURCE hDstResource,
  _In_ UINT               DstSubresource,
  _In_ D3D10DDI_HRESOURCE hSrcResource,
  _In_ UINT               SrcSubresource,
  _In_ DXGI_FORMAT        ResolveFormat
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to the display device (graphics context).</p>
</dd>

### -param <i>hDstResource</i> [in]

<dd>
<p> A handle to the destination resource to resolve to. This resource must have been created as D3D10_USAGE_DEFAULT and single sampled.</p>
</dd>

### -param <i>DstSubresource</i> [in]

<dd>
<p> An index that indicates the destination subresource to resolve to. </p>
</dd>

### -param <i>hSrcResource</i> [in]

<dd>
<p> A handle to the source resource to resolve from.</p>
</dd>

### -param <i>SrcSubresource</i> [in]

<dd>
<p> An index that indicates the source subresource to resolve from. </p>
</dd>

### -param <i>ResolveFormat</i> [in]

<dd>
<p> A DXGI_FORMAT-typed value that indicates how to interpret the contents of the resolved resource.</p>
</dd>
</dl>

## -returns
<p>None</p>

<p>The driver can use the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> callback function to set an error code. </p>

## -remarks
<p>The algorithm to resolve multiple samples to one pixel depends on the implementation. </p>

<p>The resolve operation shares similar restrictions to copy operations that occur in calls to the <a href="https://msdn.microsoft.com/9a837f42-0bea-4425-b693-dd7947ac24b1">ResourceCopy</a> and <a href="https://msdn.microsoft.com/e782dc8c-e34e-4f96-b6d9-c34d7843ed05">ResourceCopyRegion</a> functions. That is, both source and destination resources must be the same type (for example, Texture2D), and no stretching or format conversions can occur. The driver can resolve only a whole subresource; therefore, both the source and destination subresources must be equal in dimensions. Because of typeless resources, the following interactions can exist with either the source or destination resource format: </p>

<p>If each resource is prestructured plus typed, both resources must have the same format type, and that format type must match the format type that was passed in the <i>ResolveFormat</i> parameter (for example, all R32_FLOAT). </p>

<p>If one resource is prestructured plus typeless, the prestructured-plus-typed resource's format must be compatible with the typeless format, and the format type that was passed in the <i>ResolveFormat</i> parameter must match the prestructured-plus-typed format (for example, if the source format is R32_TYPELESS, and the destination format and <i>ResolveFormat</i> are R32_FLOAT). </p>

<p>If both resources are prestructured plus typeless, they must be equal formats, and the format type that was passed in the <i>ResolveFormat</i> parameter can be any format that is compatible with the typeless format. (for example, if the source and destination format are R32_TYPELESS, and <i>ResolveFormat</i> is R32_FLOAT or R32_UINT).</p>

<p>The algorithm to resolve multiple samples to one pixel depends on the implementation. </p>

<p>The resolve operation shares similar restrictions to copy operations that occur in calls to the <a href="https://msdn.microsoft.com/9a837f42-0bea-4425-b693-dd7947ac24b1">ResourceCopy</a> and <a href="https://msdn.microsoft.com/e782dc8c-e34e-4f96-b6d9-c34d7843ed05">ResourceCopyRegion</a> functions. That is, both source and destination resources must be the same type (for example, Texture2D), and no stretching or format conversions can occur. The driver can resolve only a whole subresource; therefore, both the source and destination subresources must be equal in dimensions. Because of typeless resources, the following interactions can exist with either the source or destination resource format: </p>

<p>If each resource is prestructured plus typed, both resources must have the same format type, and that format type must match the format type that was passed in the <i>ResolveFormat</i> parameter (for example, all R32_FLOAT). </p>

<p>If one resource is prestructured plus typeless, the prestructured-plus-typed resource's format must be compatible with the typeless format, and the format type that was passed in the <i>ResolveFormat</i> parameter must match the prestructured-plus-typed format (for example, if the source format is R32_TYPELESS, and the destination format and <i>ResolveFormat</i> are R32_FLOAT). </p>

<p>If both resources are prestructured plus typeless, they must be equal formats, and the format type that was passed in the <i>ResolveFormat</i> parameter can be any format that is compatible with the typeless format. (for example, if the source and destination format are R32_TYPELESS, and <i>ResolveFormat</i> is R32_FLOAT or R32_UINT).</p>

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
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/9a837f42-0bea-4425-b693-dd7947ac24b1">ResourceCopy</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e782dc8c-e34e-4f96-b6d9-c34d7843ed05">ResourceCopyRegion</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D10DDI_RESOURCERESOLVESUBRESOURCE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
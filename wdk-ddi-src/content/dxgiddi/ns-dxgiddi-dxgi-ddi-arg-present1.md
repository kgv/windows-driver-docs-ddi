---
UID: NS.dxgiddi.DXGI_DDI_ARG_PRESENT1
title: DXGI_DDI_ARG_PRESENT1
author: windows-driver-content
description: Describes a resource to display. Used with the pfnPresent1(DXGI) function by Windows Display Driver Model (WDDM) 1.3 and later user-mode display drivers.
old-location: display\dxgi_ddi_arg_present1.htm
ms.assetid: F8575652-CA6D-472E-A314-91B07C48558B
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: dxgiddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1,WDDM 1.3 and later
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGI_DDI_ARG_PRESENT1
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
ms.keywords: DXGI_DDI_ARG_PRESENT1, DXGI_DDI_ARG_PRESENT1
req.iface: 
---

# DXGI_DDI_ARG_PRESENT1 structure



## -description
<p>Describes a resource to display. Used with the <a href="https://msdn.microsoft.com/library/windows/hardware/dn469267">pfnPresent1(DXGI)</a> function by Windows Display Driver Model (WDDM) 1.3 and later user-mode display drivers.
</p>


## -syntax

````
typedef struct DXGI_DDI_ARG_PRESENT1 {
  DXGI_DDI_HRESOURCE                hSurface;
  const DXGI_DDI_ARG_PRESENTSURFACE *phSurfacesToPresent;
  UINT                              SurfacesToPresent;
  DXGI_DDI_HRESOURCE                hDstResource;
  UINT                              DstSubResourceIndex;
  void                              *pDXGIContext;
  DXGI_DDI_PRESENT_FLAGS            Flags;
  DXGI_DDI_FLIP_INTERVAL_TYPE       FlipInterval;
  UINT                              Reserved;
  const RECT                        *pDirtyRects;
  UINT                              DirtyRects;
} DXGI_DDI_ARG_PRESENT1;
````


## -struct-fields
<dl>

### -field <b>hSurface</b>

<dd>
<p>[in] A handle to the display device (graphics context) on which the driver performs the presentation. The Direct3D runtime passes this handle to the driver in the <b>hDrvDevice</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541664">D3D10DDIARG_CREATEDEVICE</a> structure when the runtime calls the driver's <a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a> function to create the display device. </p>
</dd>

### -field <b>phSurfacesToPresent</b>

<dd>
<p>[in] An array of non-<b>NULL</b> handles and zero-based indices to the source resource to display or to release. <b>phSurfacesToPresent</b> is always a valid handle for a resource to display.</p>
</dd>

### -field <b>SurfacesToPresent</b>

<dd>
<p>[in] The array of surfaces to be presented. Must not be zero.</p>
</dd>

### -field <b>hDstResource</b>

<dd>
<p>[in] A handle to the destination resource to display to. <b>hDstResource</b> can be <b>NULL</b> if the destination is unknown; kernel mode will determine the destination just before sending the hardware command stream through DMA to the graphics processor.</p>
<p>When many resource are being presented, <b>hDstResource</b> will be <b>NULL</b>, and the driver must only translate the last source resource handle for use with the <a href="https://msdn.microsoft.com/460b9be5-5817-4225-9089-f86ad64f4554">pfnPresentCb</a> function.</p>
</dd>

### -field <b>DstSubResourceIndex</b>

<dd>
<p>
      [in] The zero-based index into the destination resource, which the handle in the <b>hDstResource</b> member specifies. The <b>DstSubResourceIndex</b> index indicates the subresource or surface to display to.</p>
</dd>

### -field <b>pDXGIContext</b>

<dd>
<p>[in] A handle to the DXGI context. This handle is opaque to the driver. The driver must pass the handle in this member as the <b>pDXGIContext</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557440">DXGIDDICB_PRESENT</a> structure when the driver calls the <a href="https://msdn.microsoft.com/eefb8f2c-e460-4f9c-851d-9a97dbcd728f">pfnPresentCbDXGI</a> function. </p>
</dd>

### -field <b>Flags</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff557509">DXGI_DDI_PRESENT_FLAGS</a> structure that identifies, in bit-field flags, how to perform the present operation. </p>
</dd>

### -field <b>FlipInterval</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff557495">DXGI_DDI_FLIP_INTERVAL_TYPE</a>-typed value that indicates the flip interval (that is, if the flip occurs after zero, one, two, three, or four vertical syncs).</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved and should be set to zero.</p>
</dd>

### -field <b>pDirtyRects</b>

<dd>
<p>[in] A pointer to an array of dirty rectangles (<a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a>s), relative to the source rectangle <b>SrcRect</b>, that indicate the portion of the overlay plane that has changed.</p>
<p>The driver can use this member to perform optimizations, though it's not required to use the dirty rectangle info. However, the driver should never fail a function call based on the provided dirty rectangles.</p>
</dd>

### -field <b>DirtyRects</b>

<dd>
<p>[in] The number of dirty rectangles in the array pointed to by <b>pDirtyRects</b>.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012 R2</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>WDDM 1.3 and later</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dxgiddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557495">DXGI_DDI_FLIP_INTERVAL_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557509">DXGI_DDI_PRESENT_FLAGS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557440">DXGIDDICB_PRESENT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn469267">pfnPresent1(DXGI)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/460b9be5-5817-4225-9089-f86ad64f4554">pfnPresentCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/eefb8f2c-e460-4f9c-851d-9a97dbcd728f">pfnPresentCbDXGI</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGI_DDI_ARG_PRESENT1 structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
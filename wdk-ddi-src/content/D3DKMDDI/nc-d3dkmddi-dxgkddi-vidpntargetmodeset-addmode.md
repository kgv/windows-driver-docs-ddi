---
UID: NC.d3dkmddi.DXGKDDI_VIDPNTARGETMODESET_ADDMODE
title: DXGKDDI_VIDPNTARGETMODESET_ADDMODE
author: windows-driver-content
description: The pfnAddMode function adds a VidPN target mode to a specified VidPN target mode set object.
old-location: display\dxgk_vidpntargetmodeset_interface_pfnaddmode.htm
ms.assetid: 96c14056-aa93-4164-8adf-31fa1b3d33d3
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: dxgk_vidpntargetmodeset_interface_pfnAddMode
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
ms.keywords: DD_MULTISAMPLEQUALITYLEVELSDATA, DD_MULTISAMPLEQUALITYLEVELSDATA
req.iface: 
---

# DXGKDDI_VIDPNTARGETMODESET_ADDMODE callback



## -description
<p>The <b>pfnAddMode</b> function adds a VidPN target mode to a specified VidPN target mode set object.</p>


## -prototype

````
DXGKDDI_VIDPNTARGETMODESET_ADDMODE dxgk_vidpntargetmodeset_interface_pfnAddMode;

NTSTATUS APIENTRY dxgk_vidpntargetmodeset_interface_pfnAddMode(
  _In_ D3DKMDT_HVIDPNTARGETMODESET     hVidPnTargetModeSet,
  _In_ D3DKMDT_VIDPN_TARGET_MODE CONST *pVidPnTargetModeInfo
)
{ ... }
````


## -parameters
<dl>

### -param <i>hVidPnTargetModeSet</i> [in]

<dd>
<p>[in] A handle to a VidPN target mode set object. The display miniport driver previously obtained this handle by calling the <a href="https://msdn.microsoft.com/1b91c472-21eb-4aa8-91e3-c9eb70556d9f">pfnAcquireTargetModeSet</a> function of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> interface.</p>
</dd>

### -param <i>pVidPnTargetModeInfo</i> [in]

<dd>
<p>[in] A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a> structure that describes the target mode. The display miniport driver previously obtained this structure by calling <a href="https://msdn.microsoft.com/ebb37681-fa03-49f5-968b-87c9ff4ebae9">pfnCreateNewModeInfo</a>.</p>
</dd>
</dl>

## -returns
<p>The <b>pfnAddMode</b> function returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The function succeeded. </p><dl>
<dt><b>STATUS_GRAPHICS_INVALID_VIDPN_TARGETMODESET</b></dt>
</dl><p>The handle supplied in <i>hVidPnTargetModeSet</i> was invalid.</p>

<p> </p>

## -remarks
<p>To add a mode to a target mode set, the display miniport driver performs the following steps.</p>

<p>Call <a href="https://msdn.microsoft.com/ebb37681-fa03-49f5-968b-87c9ff4ebae9">pfnCreateNewModeInfo</a> to obtain a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a> structure. The <b>pnfCreateNewModeInfo</b> function allocates the structure and fills in the <b>Id</b> member with a newly generated target mode identifier.</p>

<p>The <b>Info</b> member of the D3DKMDT_VIDPN_TARGET_MODE structure is a <a href="https://msdn.microsoft.com/38d0a655-265b-46e0-8af3-de6757025588">D3DKMDT_VIDEO_SIGNAL_MODE</a> structure. Populate that structure with information about the mode.</p>

<p>Call <b>pfnAddMode</b> to add the mode to a target mode set.</p>

<p>The VidPN manager allocates a D3DKMDT_VIDPN_TARGET_MODE structure when you call <b>pfnCreateNewModeInfo</b>. If you add the mode described by that structure to a target mode set, you do not need to explicitly release the structure; <b>pfnAddMode</b> releases it.</p>

<p>If you obtain a D3DKMDT_VIDPN_TARGET_MODE structure by calling <b>pfnCreateNewModeInfo</b> and then decide not to add that mode to a target mode set, you must explicity release the structure by calling <a href="https://msdn.microsoft.com/0b1d0331-f0fa-40fc-a1d6-15fe3568f3cc">pfnReleaseModeInfo</a>.</p>

<p>The D3DKMDT_HVIDPNTARGETMODESET data type is defined in <i>D3dkmdt.h</i>. </p>

<p>To add a mode to a target mode set, the display miniport driver performs the following steps.</p>

<p>Call <a href="https://msdn.microsoft.com/ebb37681-fa03-49f5-968b-87c9ff4ebae9">pfnCreateNewModeInfo</a> to obtain a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a> structure. The <b>pnfCreateNewModeInfo</b> function allocates the structure and fills in the <b>Id</b> member with a newly generated target mode identifier.</p>

<p>The <b>Info</b> member of the D3DKMDT_VIDPN_TARGET_MODE structure is a <a href="https://msdn.microsoft.com/38d0a655-265b-46e0-8af3-de6757025588">D3DKMDT_VIDEO_SIGNAL_MODE</a> structure. Populate that structure with information about the mode.</p>

<p>Call <b>pfnAddMode</b> to add the mode to a target mode set.</p>

<p>The VidPN manager allocates a D3DKMDT_VIDPN_TARGET_MODE structure when you call <b>pfnCreateNewModeInfo</b>. If you add the mode described by that structure to a target mode set, you do not need to explicitly release the structure; <b>pfnAddMode</b> releases it.</p>

<p>If you obtain a D3DKMDT_VIDPN_TARGET_MODE structure by calling <b>pfnCreateNewModeInfo</b> and then decide not to add that mode to a target mode set, you must explicity release the structure by calling <a href="https://msdn.microsoft.com/0b1d0331-f0fa-40fc-a1d6-15fe3568f3cc">pfnReleaseModeInfo</a>.</p>

<p>The D3DKMDT_HVIDPNTARGETMODESET data type is defined in <i>D3dkmdt.h</i>. </p>

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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/ebb37681-fa03-49f5-968b-87c9ff4ebae9">pfnCreateNewModeInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/0b1d0331-f0fa-40fc-a1d6-15fe3568f3cc">pfnReleaseModeInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKDDI_VIDPNTARGETMODESET_ADDMODE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
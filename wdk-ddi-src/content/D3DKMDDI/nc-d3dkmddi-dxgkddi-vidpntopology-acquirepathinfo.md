---
UID: NC.d3dkmddi.DXGKDDI_VIDPNTOPOLOGY_ACQUIREPATHINFO
title: DXGKDDI_VIDPNTOPOLOGY_ACQUIREPATHINFO
author: windows-driver-content
description: The pfnAcquirePathInfo function returns a descriptor of the video present path specified by a video present source and a video present target within a particular VidPN topology.
old-location: display\dxgk_vidpntopology_interface_pfnacquirepathinfo.htm
ms.assetid: 27a03106-a5b5-489c-968a-81b3ea9940cb
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
req.alt-api: pfnAcquirePathInfo
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

# DXGKDDI_VIDPNTOPOLOGY_ACQUIREPATHINFO callback



## -description
<p>The <b>pfnAcquirePathInfo</b> function returns a descriptor of the video present path specified by a video present source and a video present target within a particular VidPN topology.</p>


## -prototype

````
DXGKDDI_VIDPNTOPOLOGY_ACQUIREPATHINFO pfnAcquirePathInfo;

NTSTATUS APIENTRY pfnAcquirePathInfo(
  _In_  const D3DKMDT_HVIDPNTOPOLOGY         hVidPnTopology,
  _In_  const D3DDDI_VIDEO_PRESENT_SOURCE_ID VidPnSourceId,
  _In_  const D3DDDI_VIDEO_PRESENT_TARGET_ID VidPnTargetId,
  _Out_ const D3DKMDT_VIDPN_PRESENT_PATH     **pVidPnPresentPathInfo
)
{ ... }
````


## -parameters
<dl>

### -param <i>hVidPnTopology</i> [in]

<dd>
<p>[in] A handle to a VidPN topology object. The display miniport driver previously obtained this handle by calling the <a href="https://msdn.microsoft.com/2bc43cd0-97a2-4120-8e6f-425664d3d28c">pfnGetTopology</a> function of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> interface.</p>
</dd>

### -param <i>VidPnSourceId</i> [in]

<dd>
<p>[in] An integer that identifies a video present source.</p>
</dd>

### -param <i>VidPnTargetId</i> [in]

<dd>
<p>[in] An integer that identifies a video present target.</p>
</dd>

### -param <i>pVidPnPresentPathInfo</i> [out]

<dd>
<p>[out] A pointer to a variable that receives a pointer to a D3DKMDT_VIDPN_PRESENT_PATH structure that describes the requested path.</p>
</dd>
</dl>

## -returns
<p>The <b>pfnAcquirePathInfo</b> function returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The function succeeded.</p><dl>
<dt><b>STATUS_GRAPHICS_INVALID_VIDPN_TOPOLOGY</b></dt>
</dl><p>The handle supplied in <i>hVidPnTopology </i>was invalid.</p>

<p> </p>

## -remarks
<p>When you have finished using the D3DKMDT_VIDPN_PRESENT_PATH structure, you must release the structure by calling <a href="https://msdn.microsoft.com/fdd34377-6b11-4005-93f1-ab42be7633c2">pfnReleasePathInfo</a>.</p>

<p>A path contains a (source, target) pair, and a topology is a collection of paths. This function returns a descriptor for the path, in a specified topology, that contains a specified (source, target) pair.</p>

<p>You can enumerate all the paths that belong to a VidPN topology object by calling <a href="https://msdn.microsoft.com/b5dc35dc-f4fb-4209-9a4d-50dc11f16216">pfnAcquireFirstPathInfo</a> and then making a sequence of calls to <b>pfnAcquireNextPathInfo</b>.</p>

<p>VidPN source identifiers are assigned by the operating system. <a href="https://msdn.microsoft.com/ffacbb39-2581-4207-841d-28ce57fbc64d">DxgkDdiStartDevice</a>, implemented by the display miniport driver, returns the number N of video present sources supported by the display adapter. Then the operating system assigns identifiers 0, 1, 2, ... N - 1.</p>

<p>VidPN target identifiers are assigned by the display miniport driver. <a href="https://msdn.microsoft.com/eb1a0df0-6239-4d82-8477-7dd015f80b6e">DxgkDdiQueryChildRelations</a>, implemented by the display miniport driver, returns an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff561001">DXGK_CHILD_DESCRIPTOR</a> structures, each of which contains an identifier.</p>

<p>The D3DKMDT_HVIDPNTOPOLOGY data type is defined in <i>D3dkmdt.h</i>.</p>

<p>The D3DDDI_VIDEO_PRESENT_SOURCE_ID and D3DDDI_VIDEO_PRESENT_TARGET_ID data types are defined in <i>D3dukmdt.h</i>. </p>

<p>When you have finished using the D3DKMDT_VIDPN_PRESENT_PATH structure, you must release the structure by calling <a href="https://msdn.microsoft.com/fdd34377-6b11-4005-93f1-ab42be7633c2">pfnReleasePathInfo</a>.</p>

<p>A path contains a (source, target) pair, and a topology is a collection of paths. This function returns a descriptor for the path, in a specified topology, that contains a specified (source, target) pair.</p>

<p>You can enumerate all the paths that belong to a VidPN topology object by calling <a href="https://msdn.microsoft.com/b5dc35dc-f4fb-4209-9a4d-50dc11f16216">pfnAcquireFirstPathInfo</a> and then making a sequence of calls to <b>pfnAcquireNextPathInfo</b>.</p>

<p>VidPN source identifiers are assigned by the operating system. <a href="https://msdn.microsoft.com/ffacbb39-2581-4207-841d-28ce57fbc64d">DxgkDdiStartDevice</a>, implemented by the display miniport driver, returns the number N of video present sources supported by the display adapter. Then the operating system assigns identifiers 0, 1, 2, ... N - 1.</p>

<p>VidPN target identifiers are assigned by the display miniport driver. <a href="https://msdn.microsoft.com/eb1a0df0-6239-4d82-8477-7dd015f80b6e">DxgkDdiQueryChildRelations</a>, implemented by the display miniport driver, returns an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff561001">DXGK_CHILD_DESCRIPTOR</a> structures, each of which contains an identifier.</p>

<p>The D3DKMDT_HVIDPNTOPOLOGY data type is defined in <i>D3dkmdt.h</i>.</p>

<p>The D3DDDI_VIDEO_PRESENT_SOURCE_ID and D3DDDI_VIDEO_PRESENT_TARGET_ID data types are defined in <i>D3dukmdt.h</i>. </p>

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
<a href="https://msdn.microsoft.com/fdd34377-6b11-4005-93f1-ab42be7633c2">pfnReleasePathInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b5dc35dc-f4fb-4209-9a4d-50dc11f16216">pfnAcquireFirstPathInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/9f09ac0e-057c-48fb-a246-35e8ed7ddfc2">pfnAcquireNextPathInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546647">D3DKMDT_VIDPN_PRESENT_PATH</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKDDI_VIDPNTOPOLOGY_ACQUIREPATHINFO callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
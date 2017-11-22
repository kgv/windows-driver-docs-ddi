---
UID: NS.d3dkmddi._DXGKARG_RECOMMENDVIDPNTOPOLOGY
title: DXGKARG_RECOMMENDVIDPNTOPOLOGY
author: windows-driver-content
description: The DXGKARG_RECOMMENDVIDPNTOPOLOGY structure contains arguments for the display miniport driver's DxgkDdiRecommendVidPnTopology function.
old-location: display\dxgkarg_recommendvidpntopology.htm
ms.assetid: 9a3efdc8-4534-4de6-89f8-42d94ba8b9a6
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGKARG_RECOMMENDVIDPNTOPOLOGY
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
ms.keywords: DXGKARG_RECOMMENDVIDPNTOPOLOGY, DXGKARG_RECOMMENDVIDPNTOPOLOGY
req.iface: 
---

# DXGKARG_RECOMMENDVIDPNTOPOLOGY structure



## -description
<p>The DXGKARG_RECOMMENDVIDPNTOPOLOGY structure contains arguments for the display miniport driver's <a href="https://msdn.microsoft.com/a7c31d2c-3893-4d25-837d-d4650aeb1cd1">DxgkDdiRecommendVidPnTopology</a> function.</p>


## -syntax

````
typedef struct _DXGKARG_RECOMMENDVIDPNTOPOLOGY {
  D3DKMDT_HVIDPN                     hVidPn;
  D3DDDI_VIDEO_PRESENT_SOURCE_ID     VidPnSourceId;
  DXGK_RECOMMENDVIDPNTOPOLOGY_REASON RequestReason;
  D3DKMDT_HVIDPNTOPOLOGY             hFallbackTopology;
} DXGKARG_RECOMMENDVIDPNTOPOLOGY;
````


## -struct-fields
<dl>

### -field <b>hVidPn</b>

<dd>
<p>A handle to a VidPN object. The <i>DxgkDdiRecommendVidPnTopology</i> function creates or augments the topology of this VidPN.</p>
</dd>

### -field <b>VidPnSourceId</b>

<dd>
<p>D3DDDI_ID_ALL or the identifier of a particular video present source on the display adapter. If this member is the identifier of a particular source, the <i>DxgkDdiRecommendVidPnTopology</i> function must augment the topology by adding at least one path that originates from that source. If this member is equal to D3DDDI_ID_ALL, <i>DxgkDdiRecommendVidPnTopology</i> must create the entire topology.</p>
</dd>

### -field <b>RequestReason</b>

<dd>
<p>
      A value from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562023">DXGK_RECOMMENDVIDPNTOPOLOGY_REASON</a> enumeration that indicates the reason that the <a href="https://msdn.microsoft.com/a7c31d2c-3893-4d25-837d-d4650aeb1cd1">DxgkDdiRecommendVidPnTopology</a> function is being called.
     </p>
</dd>

### -field <b>hFallbackTopology</b>

<dd>
<p>A handle to a VidPN topology object that represents the fallback VidPN topology that Windows will use if the miniport does not provide a topology recommendation.</p>
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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562023">DXGK_RECOMMENDVIDPNTOPOLOGY_REASON</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a7c31d2c-3893-4d25-837d-d4650aeb1cd1">DxgkDdiRecommendVidPnTopology</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_RECOMMENDVIDPNTOPOLOGY structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NS.d3dkmddi._DXGKARG_UNMAPCPUHOSTAPERTURE
title: DXGKARG_UNMAPCPUHOSTAPERTURE
author: windows-driver-content
description: The DXGKARG_UNMAPCPUHOSTAPERTURE structure is used to unmap a previously mapped range of the CPU host aperture.
old-location: display\dxgkarg_unmapcpuhostaperture.htm
ms.assetid: 22482590-B0F7-4F35-95D5-9B352810047D
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGKARG_UNMAPCPUHOSTAPERTURE
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
ms.keywords: DXGKARG_UNMAPCPUHOSTAPERTURE, DXGKARG_UNMAPCPUHOSTAPERTURE
req.iface: 
---

# DXGKARG_UNMAPCPUHOSTAPERTURE structure



## -description
<p>The <b>DXGKARG_UNMAPCPUHOSTAPERTURE</b> structure is used to unmap a previously mapped range of the CPU host aperture.</p>


## -syntax

````
typedef struct _DXGKARG_UNMAPCPUHOSTAPERTURE {
  UINT64  NumberOfPages;
  UINT32* pCpuHostAperturePages;
  WORD    SegmentId;
  WORD    PhysicalAdapterIndex;
} DXGKARG_UNMAPCPUHOSTAPERTURE;
````


## -struct-fields
<dl>

### -field <b>NumberOfPages</b>

<dd>
<p>Specifies the number of pages being unmapped.</p>
</dd>

### -field <b>pCpuHostAperturePages</b>

<dd>
<p>Array of CPU host aperture pages to unmap. This is an array of page indices from the start of the CPU host aperture physical address.</p>
</dd>

### -field <b>SegmentId</b>

<dd>
<p>The driver segment identifier (starting from 1) of the segment for which the CPU host aperture is unmapped.</p>
</dd>

### -field <b>PhysicalAdapterIndex</b>

<dd>
<p>The zero-based physical adapter index in a linked display adapter link.</p>
<div class="alert"><b>Note</b>  The page size is equal to the segment page size.</div>
<div> </div>
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
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
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
<a href="https://msdn.microsoft.com/AFE6B92F-49DB-47F9-90BC-F75B5F37178D">DxgkDdiUnmapCpuHostAperture</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_UNMAPCPUHOSTAPERTURE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
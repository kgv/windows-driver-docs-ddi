---
UID: NE.d3d10umddi.D3D10_DDI_MAP
title: D3D10_DDI_MAP
author: windows-driver-content
description: The D3D10_DDI_MAP enumeration type contains values that identify the access levels to map to a subresource in a call to the driver's ResourceMap function.
old-location: display\d3d10_ddi_map.htm
ms.assetid: f544ae60-b9c4-497c-8cb5-a2f9500a0cde
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D10_DDI_MAP
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

# D3D10_DDI_MAP enumeration



## -description
<p>The D3D10_DDI_MAP enumeration type contains values that identify the access levels to map to a subresource in a call to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function.</p>


## -syntax

````
typedef enum D3D10_DDI_MAP { 
  D3D10_DDI_MAP_READ               = 1,
  D3D10_DDI_MAP_WRITE              = 2,
  D3D10_DDI_MAP_READWRITE          = 3,
  D3D10_DDI_MAP_WRITE_DISCARD      = 4,
  D3D10_DDI_MAP_WRITE_NOOVERWRITE  = 5
} D3D10_DDI_MAP;
````


## -enum-fields
<dl>

### -field <a id="D3D10_DDI_MAP_READ"></a><a id="d3d10_ddi_map_read"></a><b>D3D10_DDI_MAP_READ</b>

<dd>
<p>Read access is requested for the CPU to the subresource.</p>
</dd>

### -field <a id="D3D10_DDI_MAP_WRITE"></a><a id="d3d10_ddi_map_write"></a><b>D3D10_DDI_MAP_WRITE</b>

<dd>
<p>Write access is requested for the CPU to the subresource.</p>
</dd>

### -field <a id="D3D10_DDI_MAP_READWRITE"></a><a id="d3d10_ddi_map_readwrite"></a><b>D3D10_DDI_MAP_READWRITE</b>

<dd>
<p>Read and write access is requested for the CPU to the subresource.</p>
</dd>

### -field <a id="D3D10_DDI_MAP_WRITE_DISCARD"></a><a id="d3d10_ddi_map_write_discard"></a><b>D3D10_DDI_MAP_WRITE_DISCARD</b>

<dd>
<p>Write access is requested for the CPU to the subresource. However, the contents of the subresource become undefined during this operation because the requesting application might completely write over the entire region of memory. You can use this access level only with dynamic resources. </p>
</dd>

### -field <a id="D3D10_DDI_MAP_WRITE_NOOVERWRITE"></a><a id="d3d10_ddi_map_write_nooverwrite"></a><b>D3D10_DDI_MAP_WRITE_NOOVERWRITE</b>

<dd>
<p>Write access is requested for the CPU to the subresource. However, the requesting application will not overwrite any data that was previously used by the GPU. You can use this access level only with dynamic vertex and index buffers. </p>
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
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D10_DDI_MAP enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
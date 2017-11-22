---
UID: NS.d3d12umddi.D3D12DDI_ALLOCATION_INFO_0022
title: D3D12DDI_ALLOCATION_INFO_0022
author: windows-driver-content
description: Specifies allocation information.
old-location: display\d3d12ddi_allocation_info_0022.htm
ms.assetid: A600C402-EB77-4C44-8349-96DAF11B807C
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d12umddi.h
req.include-header: D3d12umddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDI_ALLOCATION_INFO_0022
req.alt-loc: D3d12umddi.h
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
ms.keywords: D3D12DDI_ALLOCATION_INFO_0022, D3D12DDI_ALLOCATION_INFO_0022
req.iface: 
---

# D3D12DDI_ALLOCATION_INFO_0022 structure



## -description
<p>Specifies allocation information. </p>


## -syntax

````
typedef struct D3D12DDI_ALLOCATION_INFO_0022 {
  D3DKMT_HANDLE                       hAllocation;
  const VOID                          *pSystemMem;
  VOID                                *pPrivateDriverData;
  UINT                                PrivateDriverDataSize;
  D3DDDI_VIDEO_PRESENT_SOURCE_ID      VidPnSourceId;
  D3D12DDI_ALLOCATION_INFO_FLAGS_0022 Flags;
  D3DGPU_VIRTUAL_ADDRESS              GpuVirtualAddress;
  UINT                                Priority;
  ULONG_PTR                           Reserved[5];
} D3D12DDI_ALLOCATION_INFO_0022;
````


## -struct-fields
<dl>

### -field <b>hAllocation</b>

<dd>
<p>The handle of an allocation.</p>
</dd>

### -field <b>pSystemMem</b>

<dd>
<p>Pointer to a system memory location that is preallocated. If the allocation uses video memory, specify null. </p>
</dd>

### -field <b>pPrivateDriverData</b>

<dd>
<p>Pointer to a buffer that contains optional private driver data.</p>
</dd>

### -field <b>PrivateDriverDataSize</b>

<dd>
<p>Size of the private driver data buffer. </p>
</dd>

### -field <b>VidPnSourceId</b>

<dd>
<p>A zero-based ID of the video present source in a path of a video present network topology.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Flags that identify the type of the allocation information as a <a href="https://msdn.microsoft.com/DE3C133C-C1A9-4735-B1C4-9F6E791845A1">D3D12DDI_ALLOCATION_INFO_FLAGS_0022</a> value.</p>
</dd>

### -field <b>GpuVirtualAddress</b>

<dd>
<p>A virtual address in the GPU.</p>
</dd>

### -field <b>Priority</b>

<dd>
<p>A priority for the allocation.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d12umddi.h (include D3d12umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/DE3C133C-C1A9-4735-B1C4-9F6E791845A1">D3D12DDI_ALLOCATION_INFO_FLAGS_0022</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D12DDI_ALLOCATION_INFO_0022 structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
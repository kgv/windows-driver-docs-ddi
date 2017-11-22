---
UID: NF.d3dkmthk.D3DKMTMapGpuVirtualAddress
title: D3DKMTMapGpuVirtualAddress
author: windows-driver-content
description: D3DKMTMapGpuVirtualAddress maps a graphics processing unit (GPU) virtual address ranges to a specific allocation range or puts it to the Invalid or Zero state.
old-location: display\d3dkmtmapgpuvirtualaddress.htm
ms.assetid: 6CE8112F-1DDA-4A8B-8D3D-40DC3737976A
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Universal
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMTMapGpuVirtualAddress
req.alt-loc: GDI32.dll,API-MS-Win-DX-D3DKMT-L1-1-1.dll,GDI32.dll,API-MS-Win-DX-D3DKMT-L1-1-2.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: GDI32.lib
req.dll: GDI32.dll
req.irql: 
ms.keywords: D3DKMTMapGpuVirtualAddress
req.iface: 
---

# D3DKMTMapGpuVirtualAddress function



## -description
<p><b>D3DKMTMapGpuVirtualAddress</b> maps a graphics processing unit (GPU) virtual address ranges to a specific allocation range or puts it to the Invalid or Zero state. The driver can specify a base GPU virtual address to map or let the video memory manager automatically pick one. 
When specifying a non-NULL base address, the entire range from <b>BaseAddress</b> to <b>BaseAddress</b>+<b>Size</b> must be in a freed state or belong to a virtual address range that was obtained by calling <b>MapGpuVirtualAddress</b> or <a href="https://msdn.microsoft.com/26A827F1-1094-4A7D-9C63-758925EE6273">DxgkCbReserveGpuVirtualAddressRange</a>. Note that when <b>Protection.Zero</b> or <b>Protection.NoAccess</b> is specified, the virtual address range cannot belong to a range that was obtained by calling <b>MapGpuVirtualAddress</b>.
The driver may specify if the mapping should allow for write and execute privileges in addition to read privileges, which always exist by default. 
In the  linked display adapter configuration the paging queue defines a physical GPU, whose page tables are modified, and the allocation handle (if not NULL) defines where the page table entries are pointing to. The allocation can be resident in any physical GPU memory segment.</p>


## -syntax

````
NTSTATUS APIENTRY D3DKMTMapGpuVirtualAddress(
  _Inout_ D3DDDI_MAPGPUVIRTUALADDRESS *pData
);
````


## -parameters
<dl>

### -param <i>pData</i> [in, out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/dn906325">D3DDDI_MAPGPUVIRTUALADDRESS</a> structure that describes the operation.</p>
</dd>
</dl>

## -returns
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The device context was successfully created.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>Parameters were validated and determined to be incorrect.</p>

<p> </p>

<p>This function might also return other <b>NTSTATUS</b> values.</p>

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
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>GDI32.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>GDI32.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/26A827F1-1094-4A7D-9C63-758925EE6273">DxgkCbReserveGpuVirtualAddressRange</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMTMapGpuVirtualAddress function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
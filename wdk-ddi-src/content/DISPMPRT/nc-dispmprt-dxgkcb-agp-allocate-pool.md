---
UID: NC.dispmprt.DXGKCB_AGP_ALLOCATE_POOL
title: DXGKCB_AGP_ALLOCATE_POOL
author: windows-driver-content
description: The AgpAllocatePool function reserves, commits, and maps AGP memory.
old-location: display\agpallocatepool.htm
ms.assetid: abac76e0-eb8a-450a-a797-3733a8f71990
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: dispmprt.h
req.include-header: Dispmprt.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: AgpAllocatePool
req.alt-loc: dispmprt.h
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
ms.keywords: SYMBOL_INFO_EX, SYMBOL_INFO_EX, *PSYMBOL_INFO_EX
req.iface: IDebugSystemObjects4
---

# DXGKCB_AGP_ALLOCATE_POOL callback



## -description
<p>The <b>AgpAllocatePool</b> function reserves, commits, and maps AGP memory.</p>


## -prototype

````
DXGKCB_AGP_ALLOCATE_POOL AgpAllocatePool;

NTSTATUS APIENTRY AgpAllocatePool(
  _In_  HANDLE              Context,
  _In_  ULONG               AllocationSize,
  _In_  MEMORY_CACHING_TYPE CacheType,
  _Out_ PPHYSICAL_ADDRESS   PhysicalAddress,
  _Out_ PVOID               *VirtualAddress
)
{ ... }
````


## -parameters
<dl>

### -param <i>Context</i> [in]

<dd>
<p>A handle to a context block associated with an AGP interface. The display miniport driver previously received this handle in the <b>Context</b> member of the DXGK_AGP_INTERFACE structure that was filled in by <a href="https://msdn.microsoft.com/0ce5df90-2019-4a92-97d6-0218acc8b1e8">DxgkCbQueryServices</a>.</p>
</dd>

### -param <i>AllocationSize</i> [in]

<dd>
<p>The size, in bytes, of the AGP memory to be allocated.</p>
</dd>

### -param <i>CacheType</i> [in]

<dd>
<p>A constant from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554430">MEMORY_CACHING_TYPE</a> enumeration that specifies whether the CPU can use caching or write combining when it accesses the allocated AGP memory.</p>
</dd>

### -param <i>PhysicalAddress</i> [out]

<dd>
<p>A pointer to a PHYSICAL_ADDRESS structure that receives the base physical address of the AGP allocation. This is the base of the physical address range that the GPU will use to access the AGP memory.</p>
</dd>

### -param <i>VirtualAddress</i> [out]

<dd>
<p>A pointer to a variable that receives the base virtual address, in system space, of the AGP allocation. This is the base of the virtual address range that the CPU will use to access the AGP memory.</p>
</dd>
</dl>

## -returns
<p><b>AgpAllocatePool</b> returns STATUS_SUCCESS if it succeeds. Otherwise, it returns one of the error codes defined in <i>Ntstatus.h</i>.</p>

## -remarks
<p>Call <b>AgpAllocatePool</b> in the display miniport driver's <a href="https://msdn.microsoft.com/ffacbb39-2581-4207-841d-28ce57fbc64d">DxgkDdiStartDevice</a> function. It is likely that <b>AgpAllocatePool</b> will fail if you call it after <b>DxgkDdiStartDevice</b> has executed.</p>

<p>Call <b>AgpAllocatePool</b> in the display miniport driver's <a href="https://msdn.microsoft.com/ffacbb39-2581-4207-841d-28ce57fbc64d">DxgkDdiStartDevice</a> function. It is likely that <b>AgpAllocatePool</b> will fail if you call it after <b>DxgkDdiStartDevice</b> has executed.</p>

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
<dt>Dispmprt.h (include Dispmprt.h)</dt>
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
<a href="https://msdn.microsoft.com/6d4e957e-ad9c-45da-8d1d-0ef5f108c692">AgpFreePool</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/4440bc0f-01cb-4108-bfe8-9d5127777f00">AgpSetCommand</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560949">DXGK_AGP_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/0ce5df90-2019-4a92-97d6-0218acc8b1e8">DxgkCbQueryServices</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKCB_AGP_ALLOCATE_POOL callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
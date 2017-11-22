---
UID: NS.d3dumddi._D3DDDICB_SETPRIORITY
title: D3DDDICB_SETPRIORITY
author: windows-driver-content
description: The D3DDDICB_SETPRIORITY structure describes the priority level to which to set a resource or list of allocations.
old-location: display\d3dddicb_setpriority.htm
ms.assetid: 8d828d7b-2f86-4fe9-864c-9d0ac4b0ed65
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDICB_SETPRIORITY
req.alt-loc: d3dumddi.h
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
ms.keywords: D3DDDICB_SETPRIORITY, D3DDDICB_SETPRIORITY
req.iface: 
---

# D3DDDICB_SETPRIORITY structure



## -description
<p>The D3DDDICB_SETPRIORITY structure describes the priority level to which to set a resource or list of allocations. </p>


## -syntax

````
typedef struct _D3DDDICB_SETPRIORITY {
  HANDLE              hResource;
  UINT                NumAllocations;
  const D3DKMT_HANDLE *HandleList;
  const UINT          *pPriorities;
} D3DDDICB_SETPRIORITY;
````


## -struct-fields
<dl>

### -field <b>hResource</b>

<dd>
<p>[in] A handle to a resource whose priority must be set. If the user-mode display driver uses the array that is specified by <b>HandleList</b> to set the priority for the list of allocations, it sets <b>hResource</b> to <b>NULL</b>. If the user-mode display driver sets <b>hResource</b> to a non-<b>NULL</b> value, it must set the <b>NumAllocations</b> member to zero and <b>HandleList</b> to <b>NULL</b>. </p>
<p>If <b>hResource</b> is non-<b>NULL</b>, all of the allocations that belong to the resource are set to the priority that is specified by the first element in the array that <b>pPriorities</b> points to. </p>
</dd>

### -field <b>NumAllocations</b>

<dd>
<p>[in] The number of allocations in the <b>HandleList</b> array. If the user-mode display driver sets the handle in the <b>hResource</b> member to a non-<b>NULL</b> value, it must set <b>NumAllocations</b> to zero.</p>
</dd>

### -field <b>HandleList</b>

<dd>
<p>[in] An array of D3DKMT_HANDLE data types that represent kernel-mode handles to the allocations. The Microsoft Direct3D runtime's <a href="https://msdn.microsoft.com/a61e6c6a-3992-429c-ad8c-5f1a61dc7b8b">pfnAllocateCb</a> function returns these handles. Therefore, the user-mode display driver uses these handles to set priority for the allocations.</p>
<p>If the user-mode display driver sets the handle in the <b>hResource</b> member to a non-<b>NULL</b> value, it must set <b>HandleList</b> to <b>NULL</b>. </p>
</dd>

### -field <b>pPriorities</b>

<dd>
<p>[in] A pointer to an array of priority levels. If the <b>hResource</b> member is non-<b>NULL</b>, the array must contain a single element. If <b>hResource</b> is <b>NULL</b>, the number of elements in the array is specified by the <b>NumAllocations</b> member, and each allocation in the array that is specified by <b>HandleList</b> is set to the priority level of the corresponding element in <b>pPriorities</b>. For a list of defined priority levels, see the Remarks section of the <a href="https://msdn.microsoft.com/1812cb0f-9232-4813-9c7b-74c9fa4d03cf">pfnSetPriorityCb</a> reference page.</p>
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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/a61e6c6a-3992-429c-ad8c-5f1a61dc7b8b">pfnAllocateCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1812cb0f-9232-4813-9c7b-74c9fa4d03cf">pfnSetPriorityCb</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDICB_SETPRIORITY structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
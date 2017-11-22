---
UID: NC.d3dumddi.PFND3DDDI_RENAME
title: PFND3DDDI_RENAME
author: windows-driver-content
description: The Rename function informs a user-mode display driver to start using the renamed allocation that the LockAsync function previously returned for the specified resource.
old-location: display\rename.htm
ms.assetid: 60f733e1-d376-4372-b1cc-39508b3a98e5
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: Rename
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
ms.keywords: DXGK_MIRACAST_CHUNK_INFO, DXGK_MIRACAST_CHUNK_INFO
req.iface: 
---

# PFND3DDDI_RENAME callback



## -description
<p>The <i>Rename</i> function informs a user-mode display driver to start using the renamed allocation that the <a href="https://msdn.microsoft.com/c8f76ebe-947a-45e4-abbc-f6020da929e8">LockAsync</a> function previously returned for the specified resource.</p>


## -prototype

````
PFND3DDDI_RENAME Rename;

__checkReturn HRESULT APIENTRY Rename(
  _In_       HANDLE           hDevice,
  _In_ const D3DDDIARG_RENAME *pData
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to a display device (that is, the graphics context).</p>
</dd>

### -param <i>pData</i> [in]

<dd>
<p> A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543262">D3DDDIARG_RENAME</a> structure that describes the resource or surface within a resource to rename with a new allocation.</p>
</dd>
</dl>

## -returns
<p><i>Rename</i> returns one of the following values:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The resource is successfully renamed.</p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p><i>Rename</i> could not allocate the required memory for it to complete.</p>

<p> </p>

## -remarks
<p>On multiple-processor computers, the Microsoft Direct3D runtime calls the user-mode display driver's <i>Rename</i> function from a worker thread instead of from the main application thread. The runtime calls <i>Rename</i>, at most, once for each successful call to the driver's <a href="https://msdn.microsoft.com/c8f76ebe-947a-45e4-abbc-f6020da929e8">LockAsync</a> function with the <b>Discard</b> bit-field flag set in the <b>Flags</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543213">D3DDDIARG_LOCKASYNC</a> structure that the <i>pData</i> parameter of <i>LockAsync</i> points to. </p>

<p><i>Rename</i> informs the driver to start using the renamed allocation that is specified by the <b>hCookie</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543262">D3DDDIARG_RENAME</a> structure that the <i>pData</i> parameter of <i>Rename</i> points to. The <b>hCookie</b> handle was previously returned by the <a href="https://msdn.microsoft.com/c8f76ebe-947a-45e4-abbc-f6020da929e8">LockAsync</a> function if the <b>Discard</b> bit-field flag was set for the locked resource. </p>

<p>After <i>Rename</i> returns successfully (with S_OK), the user-mode display driver should use the allocation that <b>hCookie</b> specifies for all rendering operations that reference the resource that the <b>hResource</b> and <b>SubResourceIndex</b> members of D3DDDIARG_RENAME specify.</p>

<p>On multiple-processor computers, the Microsoft Direct3D runtime calls the user-mode display driver's <i>Rename</i> function from a worker thread instead of from the main application thread. The runtime calls <i>Rename</i>, at most, once for each successful call to the driver's <a href="https://msdn.microsoft.com/c8f76ebe-947a-45e4-abbc-f6020da929e8">LockAsync</a> function with the <b>Discard</b> bit-field flag set in the <b>Flags</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543213">D3DDDIARG_LOCKASYNC</a> structure that the <i>pData</i> parameter of <i>LockAsync</i> points to. </p>

<p><i>Rename</i> informs the driver to start using the renamed allocation that is specified by the <b>hCookie</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543262">D3DDDIARG_RENAME</a> structure that the <i>pData</i> parameter of <i>Rename</i> points to. The <b>hCookie</b> handle was previously returned by the <a href="https://msdn.microsoft.com/c8f76ebe-947a-45e4-abbc-f6020da929e8">LockAsync</a> function if the <b>Discard</b> bit-field flag was set for the locked resource. </p>

<p>After <i>Rename</i> returns successfully (with S_OK), the user-mode display driver should use the allocation that <b>hCookie</b> specifies for all rendering operations that reference the resource that the <b>hResource</b> and <b>SubResourceIndex</b> members of D3DDDIARG_RENAME specify.</p>

## -requirements
<table>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544519">D3DDDI_DEVICEFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543213">D3DDDIARG_LOCKASYNC</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543262">D3DDDIARG_RENAME</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c8f76ebe-947a-45e4-abbc-f6020da929e8">LockAsync</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/60f733e1-d376-4372-b1cc-39508b3a98e5">Rename</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_RENAME callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
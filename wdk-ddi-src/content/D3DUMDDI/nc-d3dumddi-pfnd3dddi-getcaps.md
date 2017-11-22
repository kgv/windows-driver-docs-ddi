---
UID: NC.d3dumddi.PFND3DDDI_GETCAPS
title: PFND3DDDI_GETCAPS
author: windows-driver-content
description: The GetCaps function queries for capabilities of the graphics adapter.
old-location: display\getcaps.htm
ms.assetid: cf6c61ce-7b53-46d0-b3ff-ed5b2b964c65
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GetCaps
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

# PFND3DDDI_GETCAPS callback



## -description
<p>The <i>GetCaps</i> function queries for capabilities of the graphics adapter.</p>


## -prototype

````
PFND3DDDI_GETCAPS GetCaps;

__checkReturn HRESULT APIENTRY GetCaps(
  _In_          HANDLE            hAdapter,
  _Inout_ const D3DDDIARG_GETCAPS *pData
)
{ ... }
````


## -parameters
<dl>

### -param <i>hAdapter</i> [in]

<dd>
<p> A handle that identifies the graphics adapter. </p>
</dd>

### -param <i>pData</i> [in, out]

<dd>
<p> A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> structure that describes the capabilities to retrieve.</p>
</dd>
</dl>

## -returns
<p><i>GetCaps</i> returns one of the following values:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The capabilities were successfully retrieved.</p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p>
<a href="https://msdn.microsoft.com/cf6c61ce-7b53-46d0-b3ff-ed5b2b964c65">GetCaps</a> could not allocate the required memory for it to complete.</p>

<p> </p>

## -remarks
<p>The data that is returned by the <i>GetCaps</i> function in the <b>pData</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> structure depends on the type of data that is requested (that is, the data depends on the <b>Type</b> member of <b>D3DDDIARG_GETCAPS</b> and sometimes on the <b>pInfo</b> member).</p>

<p>Here are examples of how to set up the <i>GetCaps</i> call depending on the value of <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a>.<b>Type</b>.</p>

<p> </p>

<p>See the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> enumeration topic for explanations of other values for <b>D3DDDIARG_GETCAPS</b>.<b>Type</b> that are used for multiplane overlays.</p>

<p>If a Microsoft Direct3D Level 9 driver that supports Windows Display Driver Model (WDDM) 1.3 and later completes a call to <i>GetCaps</i> and returns <b>S_OK</b> but doesn't change the data in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> structure, it indicates to the Direct3D runtime that the hardware and driver don't support simple instancing. For more info, see <a href="https://msdn.microsoft.com/library/windows/hardware/dn465882">D3DDDICAPS_SIMPLE_INSTANCING_SUPPORT</a>.</p>

<p>The data that is returned by the <i>GetCaps</i> function in the <b>pData</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> structure depends on the type of data that is requested (that is, the data depends on the <b>Type</b> member of <b>D3DDDIARG_GETCAPS</b> and sometimes on the <b>pInfo</b> member).</p>

<p>Here are examples of how to set up the <i>GetCaps</i> call depending on the value of <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a>.<b>Type</b>.</p>

<p> </p>

<p>See the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> enumeration topic for explanations of other values for <b>D3DDDIARG_GETCAPS</b>.<b>Type</b> that are used for multiplane overlays.</p>

<p>If a Microsoft Direct3D Level 9 driver that supports Windows Display Driver Model (WDDM) 1.3 and later completes a call to <i>GetCaps</i> and returns <b>S_OK</b> but doesn't change the data in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a> structure, it indicates to the Direct3D runtime that the hardware and driver don't support simple instancing. For more info, see <a href="https://msdn.microsoft.com/library/windows/hardware/dn465882">D3DDDICAPS_SIMPLE_INSTANCING_SUPPORT</a>.</p>

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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544355">D3DDDI_ADAPTERFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543148">D3DDDIARG_GETCAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn465882">D3DDDICAPS_SIMPLE_INSTANCING_SUPPORT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544312">D3DDDIFORMAT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550275">DDRAW_CAPS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_GETCAPS callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
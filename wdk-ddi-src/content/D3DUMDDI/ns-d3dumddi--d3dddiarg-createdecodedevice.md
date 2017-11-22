---
UID: NS.d3dumddi._D3DDDIARG_CREATEDECODEDEVICE
title: D3DDDIARG_CREATEDECODEDEVICE
author: windows-driver-content
description: The D3DDDIARG_CREATEDECODEDEVICE structure describes a Microsoft DirectX Video Acceleration (DirectX VA) decode device to create.
old-location: display\d3dddiarg_createdecodedevice.htm
ms.assetid: 15750301-da36-4341-8d5a-ab76a2edb970
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
req.alt-api: D3DDDIARG_CREATEDECODEDEVICE
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
ms.keywords: D3DDDIARG_CREATEDECODEDEVICE, D3DDDIARG_CREATEDECODEDEVICE
req.iface: 
---

# D3DDDIARG_CREATEDECODEDEVICE structure



## -description
<p>The D3DDDIARG_CREATEDECODEDEVICE structure describes a Microsoft DirectX Video Acceleration (DirectX VA) decode device to create. </p>


## -syntax

````
typedef struct _D3DDDIARG_CREATEDECODEDEVICE {
  const GUID                  *pGuid;
  DXVADDI_VIDEODESC           VideoDesc;
  DXVADDI_CONFIGPICTUREDECODE *pConfig;
  HANDLE                      hDecode;
} D3DDDIARG_CREATEDECODEDEVICE;
````


## -struct-fields
<dl>

### -field <b>pGuid</b>

<dd>
<p>[in] A pointer to the GUID that represents the DirectX VA decode type. The Microsoft Direct3D runtime calls the <a href="https://msdn.microsoft.com/cf6c61ce-7b53-46d0-b3ff-ed5b2b964c65">GetCaps</a> function to query for the supported GUIDs.</p>
</dd>

### -field <b>VideoDesc</b>

<dd>
<p>[in] The <a href="https://msdn.microsoft.com/library/windows/hardware/ff562944">DXVADDI_VIDEODESC</a> structure for the video stream that the decode device should decode.</p>
</dd>

### -field <b>pConfig</b>

<dd>
<p>[in] A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562894">DXVADDI_CONFIGPICTUREDECODE</a> structure that contains the DirectX VA connection configuration data for compressed picture decoding that the decode device requires. The Direct3D runtime calls the <a href="https://msdn.microsoft.com/cf6c61ce-7b53-46d0-b3ff-ed5b2b964c65">GetCaps</a> function to query for the supported configurations.</p>
</dd>

### -field <b>hDecode</b>

<dd>
<p>[in/out] A handle to the decode device. The user-mode display driver must set this handle to a value that the Direct3D runtime can use to identify the decode device in subsequent calls.</p>
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
<a href="https://msdn.microsoft.com/4d9a062a-2fdf-4e55-a335-c03c5d5665ff">CreateDecodeDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562894">DXVADDI_CONFIGPICTUREDECODE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562944">DXVADDI_VIDEODESC</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/cf6c61ce-7b53-46d0-b3ff-ed5b2b964c65">GetCaps</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDIARG_CREATEDECODEDEVICE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
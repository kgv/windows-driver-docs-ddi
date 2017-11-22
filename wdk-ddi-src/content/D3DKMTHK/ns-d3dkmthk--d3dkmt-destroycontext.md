---
UID: NS.d3dkmthk._D3DKMT_DESTROYCONTEXT
title: D3DKMT_DESTROYCONTEXT
author: windows-driver-content
description: The D3DKMT_DESTROYCONTEXT structure contains a handle to a kernel-mode device context to release.
old-location: display\d3dkmt_destroycontext.htm
ms.assetid: 116c0fa7-ac3c-4a56-804c-637514a19c73
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_DESTROYCONTEXT
req.alt-loc: d3dkmthk.h
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
ms.keywords: D3DKMT_DESTROYCONTEXT, D3DKMT_DESTROYCONTEXT
req.iface: 
---

# D3DKMT_DESTROYCONTEXT structure



## -description
<p>The D3DKMT_DESTROYCONTEXT structure contains a handle to a kernel-mode device context to release.</p>


## -syntax

````
typedef struct _D3DKMT_DESTROYCONTEXT {
  D3DKMT_HANDLE hContext;
} D3DKMT_DESTROYCONTEXT;
````


## -struct-fields
<dl>

### -field <b>hContext</b>

<dd>
<p>[in] A handle to the device context that the Microsoft DirectX graphics kernel subsystem (<i>Dxgkrnl.sys</i>) supplied and that is returned from the call to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546814">D3DKMTCreateContext</a> function.</p>
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
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546814">D3DKMTCreateContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546897">D3DKMTDestroyContext</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_DESTROYCONTEXT structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
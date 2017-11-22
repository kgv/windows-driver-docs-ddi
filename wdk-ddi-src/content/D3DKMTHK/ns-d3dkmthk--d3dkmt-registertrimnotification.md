---
UID: NS.d3dkmthk._D3DKMT_REGISTERTRIMNOTIFICATION
title: D3DKMT_REGISTERTRIMNOTIFICATION
author: windows-driver-content
description: D3DKMT_REGISTERTRIMNOTIFICATION is used with D3DKMTRegisterTrimNotification to register a callback for a kernel mode device for notifications from a graphics framework (such as OpenGL).
old-location: display\d3dkmt_registertrimnotification.htm
ms.assetid: CA5BC76B-539E-4FFF-8E02-C475D18588F6
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_REGISTERTRIMNOTIFICATION
req.alt-loc: D3dkmthk.h
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
ms.keywords: D3DKMT_REGISTERTRIMNOTIFICATION, D3DKMT_REGISTERTRIMNOTIFICATION
req.iface: 
---

# D3DKMT_REGISTERTRIMNOTIFICATION structure



## -description
<p><b>D3DKMT_REGISTERTRIMNOTIFICATION</b> is used with <a href="https://msdn.microsoft.com/library/windows/hardware/dn906781">D3DKMTRegisterTrimNotification</a> to register a callback for a kernel mode device for notifications from a graphics framework (such as OpenGL).

</p>


## -syntax

````
typedef struct _D3DKMT_REGISTERTRIMNOTIFICATION {
  LUID                               AdapterLuid;
  D3DKMT_HANDLE                      hDevice;
  PFND3DKMT_TRIMNOTIFICATIONCALLBACK Callback;
  VOID                               *Context;
  VOID                               *Handle;
} D3DKMT_REGISTERTRIMNOTIFICATION;
````


## -struct-fields
<dl>

### -field <b>AdapterLuid</b>

<dd>
<p>[in] Luid of the adapter which the device created.</p>
</dd>

### -field <b>hDevice</b>

<dd>
<p>[in] Device to trim the residency list for.</p>
</dd>

### -field <b>Callback</b>

<dd>
<p>[in] Pointer to the callback function.</p>
</dd>

### -field <b>Context</b>

<dd>
<p>[in] Caller-supplied context for callback.</p>
</dd>

### -field <b>Handle</b>

<dd>
<p>[out] Handle that will be used to unregister the callback with <a href="https://msdn.microsoft.com/library/windows/hardware/dn906787">D3DKMTUnregisterTrimNotification</a>.</p>
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
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn906781">D3DKMTRegisterTrimNotification</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn906787">D3DKMTUnregisterTrimNotification</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_REGISTERTRIMNOTIFICATION structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
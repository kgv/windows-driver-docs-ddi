---
UID: NS.d3dkmddi._DXGKARG_QUERYCURRENTFENCE
title: DXGKARG_QUERYCURRENTFENCE
author: windows-driver-content
description: The DXGKARG_QUERYCURRENTFENCE structure describes the latest completed submission fence.
old-location: display\dxgkarg_querycurrentfence.htm
ms.assetid: 84a7c49b-d079-4d14-b371-5cfb75c1331c
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGKARG_QUERYCURRENTFENCE
req.alt-loc: d3dkmddi.h
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
ms.keywords: DXGKARG_QUERYCURRENTFENCE, DXGKARG_QUERYCURRENTFENCE
req.iface: 
---

# DXGKARG_QUERYCURRENTFENCE structure



## -description
<p>The DXGKARG_QUERYCURRENTFENCE structure describes the latest completed submission fence. </p>


## -syntax

````
typedef struct _DXGKARG_QUERYCURRENTFENCE {
  UINT CurrentFence;
  UINT NodeOrdinal;
  UINT EngineOrdinal;
} DXGKARG_QUERYCURRENTFENCE;
````


## -struct-fields
<dl>

### -field <b>CurrentFence</b>

<dd>
<p>[out] The current fence data.</p>
</dd>

### -field <b>NodeOrdinal</b>

<dd>
<p>[in] The zero-based index of the node for the current fence.</p>
</dd>

### -field <b>EngineOrdinal</b>

<dd>
<p>[in] The zero-based index of the engine, within the node that <b>NodeOrdinal</b> specifies, for the current fence.</p>
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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/0ca4d42f-3036-4b81-91a4-fbce7ac891fe">DxgkDdiQueryCurrentFence</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_QUERYCURRENTFENCE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
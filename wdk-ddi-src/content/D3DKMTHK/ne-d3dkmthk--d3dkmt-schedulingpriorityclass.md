---
UID: NE.d3dkmthk._D3DKMT_SCHEDULINGPRIORITYCLASS
title: D3DKMT_SCHEDULINGPRIORITYCLASS
author: windows-driver-content
description: The D3DKMT_SCHEDULINGPRIORITYCLASS enumeration type contains values that describe the scheduling priority for a process.
old-location: display\d3dkmt_schedulingpriorityclass.htm
ms.assetid: d42e37d0-0ba9-4b79-903d-fdbb478ab196
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_SCHEDULINGPRIORITYCLASS
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
ms.keywords: DXGKMDT_OPM_STANDARD_INFORMATION, DXGKMDT_OPM_STANDARD_INFORMATION
req.iface: 
---

# D3DKMT_SCHEDULINGPRIORITYCLASS enumeration



## -description
<p>The D3DKMT_SCHEDULINGPRIORITYCLASS enumeration type contains values that describe the scheduling priority for a process.</p>


## -syntax

````
typedef enum _D3DKMT_SCHEDULINGPRIORITYCLASS { 
  D3DKMT_SCHEDULINGPRIORITYCLASS_IDLE          = 0,
  D3DKMT_SCHEDULINGPRIORITYCLASS_BELOW_NORMAL  = 1,
  D3DKMT_SCHEDULINGPRIORITYCLASS_NORMAL        = 2,
  D3DKMT_SCHEDULINGPRIORITYCLASS_ABOVE_NORMAL  = 3,
  D3DKMT_SCHEDULINGPRIORITYCLASS_HIGH          = 4,
  D3DKMT_SCHEDULINGPRIORITYCLASS_REALTIME      = 5
} D3DKMT_SCHEDULINGPRIORITYCLASS;
````


## -enum-fields
<dl>

### -field <a id="D3DKMT_SCHEDULINGPRIORITYCLASS_IDLE"></a><a id="d3dkmt_schedulingpriorityclass_idle"></a><b>D3DKMT_SCHEDULINGPRIORITYCLASS_IDLE</b>

<dd>
<p>The process is idle.</p>
</dd>

### -field <a id="D3DKMT_SCHEDULINGPRIORITYCLASS_BELOW_NORMAL"></a><a id="d3dkmt_schedulingpriorityclass_below_normal"></a><b>D3DKMT_SCHEDULINGPRIORITYCLASS_BELOW_NORMAL</b>

<dd>
<p>The scheduling priority of the process is below normal.</p>
</dd>

### -field <a id="D3DKMT_SCHEDULINGPRIORITYCLASS_NORMAL"></a><a id="d3dkmt_schedulingpriorityclass_normal"></a><b>D3DKMT_SCHEDULINGPRIORITYCLASS_NORMAL</b>

<dd>
<p>The scheduling priority of the process is normal.</p>
</dd>

### -field <a id="D3DKMT_SCHEDULINGPRIORITYCLASS_ABOVE_NORMAL"></a><a id="d3dkmt_schedulingpriorityclass_above_normal"></a><b>D3DKMT_SCHEDULINGPRIORITYCLASS_ABOVE_NORMAL</b>

<dd>
<p>The scheduling priority of the process is above normal.</p>
</dd>

### -field <a id="D3DKMT_SCHEDULINGPRIORITYCLASS_HIGH"></a><a id="d3dkmt_schedulingpriorityclass_high"></a><b>D3DKMT_SCHEDULINGPRIORITYCLASS_HIGH</b>

<dd>
<p>The scheduling priority of the process is high.</p>
</dd>

### -field <a id="D3DKMT_SCHEDULINGPRIORITYCLASS_REALTIME"></a><a id="d3dkmt_schedulingpriorityclass_realtime"></a><b>D3DKMT_SCHEDULINGPRIORITYCLASS_REALTIME</b>

<dd>
<p>The scheduling priority of the process is in real time.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546992">D3DKMTGetProcessSchedulingPriorityClass</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547182">D3DKMTSetProcessSchedulingPriorityClass</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_SCHEDULINGPRIORITYCLASS enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
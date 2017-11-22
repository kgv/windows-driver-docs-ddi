---
UID: NS.d3dkmddi._DXGK_CONNECTION_CHANGE
title: DXGK_CONNECTION_CHANGE
author: windows-driver-content
description: Structure to describe the most recently updated status of the link for a target.
old-location: display\dxgk_connection_change.htm
ms.assetid: 0B0D640C-3E4B-4DE0-AA11-C751F210C77A
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_CONNECTION_CHANGE
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
ms.keywords: DXGK_CONNECTION_CHANGE, DXGK_CONNECTION_CHANGE, *PDXGK_CONNECTION_CHANGE
req.iface: 
---

# DXGK_CONNECTION_CHANGE structure



## -description
<p>Structure to describe the most recently updated status of the link for a target.</p>


## -syntax

````
typedef struct _DXGK_CONNECTION_CHANGE {
  ULONGLONG                      ConnectionChangeId  :24;
  D3DDDI_VIDEO_PRESENT_TARGET_ID TargetId  :4;
  DXGK_CONNECTION_STATUS         ConnectionStatus  :4;
  ULONG                          Reserved;
  union {
    struct {
      D3DKMDT_VIDEO_OUTPUT_TECHNOLOGY MonitorConnect.LinkTargetType;
    } MonitorConnect;
    struct {
      D3DKMDT_VIDEO_OUTPUT_TECHNOLOGY TargetConnect.BaseTargetType;
      D3DDDI_VIDEO_PRESENT_TARGET_ID  TargetConnect.NewTargetId;
    } TargetConnect;
    struct {
      D3DKMDT_VIDEO_OUTPUT_TECHNOLOGY TargetJoin.BaseTargetType;
      D3DDDI_VIDEO_PRESENT_TARGET_ID  TargetJoin.NewTargetId;
    } TargetJoin;
  };
} DXGK_CONNECTION_CHANGE, *PDXGK_CONNECTION_CHANGE;
````


## -struct-fields
<dl>

### -field <b>ConnectionChangeId</b>

<dd>
<p>The per target unique id for the transition being reported.  This value must be unique across all targets on the adapter and must be monotonically increasing for each change reported.</p>
</dd>

### -field <b>TargetId</b>

<dd>
<p>The target id for which the change is being reported.  This target id must have been reported to the OS before and must be in a state which supports the given change.</p>
</dd>

### -field <b>ConnectionStatus</b>

<dd>
<p>The status of the connection.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This value is reserved for system use.</p>
</dd>

### -field <b>MonitorConnect</b>

<dd>
<dl>

### -field <b>MonitorConnect.LinkTargetType</b>

<dd>
<p>This is the video output technology of the monitor which has been connected.  Internal and Miracast are not allowed so only the following values are allowed:</p>
<dl>
<dd>D3DKMDT_VOT_OTHER</dd>
<dd>D3DKMDT_VOT_HD15</dd>
<dd>D3DKMDT_VOT_SVIDEO</dd>
<dd>D3DKMDT_VOT_COMPOSITE_VIDEO</dd>
<dd>D3DKMDT_VOT_COMPONENT_VIDEO</dd>
<dd>D3DKMDT_VOT_DVI</dd>
<dd>D3DKMDT_VOT_HDMI</dd>
<dd>D3DKMDT_VOT_D_JPN</dd>
<dd>D3DKMDT_VOT_SDI</dd>
<dd>D3DKMDT_VOT_DISPLAYPORT_EXTERNAL</dd>
<dd>D3DKMDT_VOT_UDI_EXTERNAL</dd>
<dd>D3DKMDT_VOT_SDTVDONGLE</dd>
</dl>
</dd>
</dl>
</dd>

### -field <b>TargetConnect</b>

<dd>
<dl>

### -field <b>TargetConnect.BaseTargetType</b>

<dd>
<p>This is the video output technology of connector of the new target.  As with MonitorConnect.LinkTargetType,  Internal and Miracast are not allowed so the same target types as listed above are allowed.</p>
</dd>

### -field <b>TargetConnect.NewTargetId</b>

<dd>
<p>The target id for which the change is being reported.  This target id must have been reported to the OS before and must be in a state which supports the given change.  </p>
</dd>
</dl>
</dd>

### -field <b>TargetJoin</b>

<dd>
<dl>

### -field <b>TargetJoin.BaseTargetType</b>

<dd>
<p>This is the video output technology of the connector of the new target.  As with MonitorConnect.LinkTargetType,  Internal and Miracast are not allowed so the same target types as listed above are allowed.  </p>
<div class="alert"><b>Note</b>  The same BaseTargetType must be reported for all targets which are being joined to each other.</div>
<div> </div>
</dd>

### -field <b>TargetJoin.NewTargetId</b>

<dd>
<p>The target id for which the change is being reported.  This target id must have been reported to the OS before and must be in a state which supports the given change.  </p>
</dd>
</dl>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmddi.h</dt>
</dl>
</td>
</tr>
</table>
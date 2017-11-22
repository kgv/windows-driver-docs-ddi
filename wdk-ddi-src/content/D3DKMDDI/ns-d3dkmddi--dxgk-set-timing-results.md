---
UID: NS.d3dkmddi._DXGK_SET_TIMING_RESULTS
title: DXGK_SET_TIMING_RESULTS
author: windows-driver-content
description: Structure to report result flags from the SetTiming call which apply to the complete call rather than individual paths.
old-location: display\dxgk_set_timing_results.htm
ms.assetid: EA5C845B-76FD-40AD-B4E8-78601CA847CE
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
req.alt-api: DXGK_SET_TIMING_RESULTS
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
ms.keywords: DXGK_SET_TIMING_RESULTS, DXGK_SET_TIMING_RESULTS, *PDXGK_SET_TIMING_RESULTS
req.iface: 
---

# DXGK_SET_TIMING_RESULTS structure



## -description
<p>Structure to report result flags from the SetTiming call which apply to the complete call rather than individual paths.</p>


## -syntax

````
typedef struct _DXGK_SET_TIMING_RESULTS {
  union {
    struct {
      UINT ConnectionStatusChanges  :1;
      UINT Reserved  :31;
    };
    UINT Value;
  };
} DXGK_SET_TIMING_RESULTS, *PDXGK_SET_TIMING_RESULTS;
````


## -struct-fields
<dl>

### -field <b>ConnectionStatusChanges</b>

<dd>
<p>If set, indicates that one or more connector status changes were detected in the course of this call so the OS needs to call DxgkDdiQueryConnectionStatus to catch up with all changes and to resync with the current state.  </p>
<div class="alert"><b>Note</b>  This flag is intended to indicate to the OS that a change in available displays has occurred so TargetStatus* and MonitorStatus* changes should cause the driver to set the flag whereas LinkConfiguration* changes should be reported but should not cause the flag to be set.  Any update to an active path requires that a LinkConfiguration* change be reported so that the status of the change can be distinguished from previous changes with the same result so including these changes in the flag would not provide useful information.</div>
<div> </div>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This value is reserved for system use.</p>
</dd>

### -field <b>Value</b>

<dd>
<p>UINT used to operate on the combined bit-fields.</p>
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
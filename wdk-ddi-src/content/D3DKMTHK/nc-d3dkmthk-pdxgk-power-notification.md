---
UID: NC.d3dkmthk.PDXGK_POWER_NOTIFICATION
title: PDXGK_POWER_NOTIFICATION
author: windows-driver-content
description: A callback providing notification that the graphics device will be undergoing a device power state transition.
old-location: display\pdxgk_power_notification.htm
ms.assetid: 11549B4E-7929-4957-9775-BF8AAF501D45
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: *PDXGK_POWER_NOTIFICATION
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

# PDXGK_POWER_NOTIFICATION callback



## -description
<p>A callback providing notification that the graphics device will be undergoing a device power state transition.</p>


## -prototype

````
VOID *PDXGK_POWER_NOTIFICATION(
   PVOID              GraphicsDeviceHandle,
   DEVICE_POWER_STATE NewGrfxPowerState,
   BOOLEAN            PreNotification
);
````


## -parameters
<dl>

### -param <i>GraphicsDeviceHandle</i> 

<dd>
<p>A handle to the graphics device.</p>
</dd>

### -param <i>NewGrfxPowerState</i> 

<dd>
<p>Indicates the new graphics power state.</p>
</dd>

### -param <i>PreNotification</i> 

<dd>
<p>Indicates that a notification should be provided.</p>
</dd>
</dl>

## -returns
<p>This callback function does not return a value.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmthk.h</dt>
</dl>
</td>
</tr>
</table>
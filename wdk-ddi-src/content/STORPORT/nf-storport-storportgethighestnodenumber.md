---
UID: NF.storport.StorPortGetHighestNodeNumber
title: StorPortGetHighestNodeNumber
author: windows-driver-content
description: The StorPortGetHighestNodeNumber routine returns the largest possible node number on the system.
old-location: storage\storportgethighestnodenumber.htm
ms.assetid: 3e0b85f9-b6e4-4d53-b8dc-7f51e0f74be3
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortGetHighestNodeNumber
req.alt-loc: storport.h
req.ddi-compliance: StorPortIrql
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: StorPortGetHighestNodeNumber
req.iface: 
req.product: Windows 10 or later.
---

# StorPortGetHighestNodeNumber function



## -description
<p>The <b>StorPortGetHighestNodeNumber</b> routine returns the largest possible node number on the system.</p>


## -syntax

````
ULONG StorPortGetHighestNodeNumber(
  _In_  PVOID  HwDeviceExtension,
  _Out_ PULONG HighestNode
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension for the host bus adapter (HBA).</p>
</dd>

### -param <i>HighestNode</i> [out]

<dd>
<p>A pointer to a variable that holds the highest-numbered node.</p>
</dd>
</dl>

## -returns
<p>The <b>StorPortGetHighestNodeNumber</b>routine returns one of the following status codes:</p><dl>
<dt><b>STOR_STATUS_NOT_IMPLEMENTED</b></dt>
</dl><p>This function is not implemented on the active operating system.</p><dl>
<dt><b>STOR_STATUS_SUCCESS</b></dt>
</dl><p>The operation was successful.</p><dl>
<dt><b>STOR_STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The operation fails with this return value if one or more of the parameters are invalid, for example, if <i>HighestNode</i> is set to <b>NULL</b>.</p>

<p> </p>

## -remarks


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
<p>Available in Windows 7 and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454266">StorPortIrql</a>
</td>
</tr>
</table>
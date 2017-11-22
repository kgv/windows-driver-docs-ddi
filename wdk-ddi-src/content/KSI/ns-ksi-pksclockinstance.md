---
UID: NS.ksi.PKSCLOCKINSTANCE
title: PKSCLOCKINSTANCE
author: windows-driver-content
description: TBD.
old-location: stream\ksclockinstance.htm
ms.assetid: DC8A7CE9-7FDE-4FC9-8C71-3F3368E7E5C1
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ksi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSCLOCKINSTANCE
req.alt-loc: 
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
ms.keywords: PKSCLOCKINSTANCE, KSCLOCKINSTANCE, *PKSCLOCKINSTANCE
req.iface: 
---

# PKSCLOCKINSTANCE structure



## -description
<p>TBD</p>


## -syntax

````
typedef struct {
  KSOBJECT_HEADER  Header;
  PKISDEFAULTCLOCK DefaultClock;
  ULONG            Reserved;
} KSCLOCKINSTANCE, *PKSCLOCKINSTANCE;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>TBD</p>
</dd>

### -field <b>DefaultClock</b>

<dd>
<p>TBD</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>TBD</p>
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
<dt>Ksi.h</dt>
</dl>
</td>
</tr>
</table>
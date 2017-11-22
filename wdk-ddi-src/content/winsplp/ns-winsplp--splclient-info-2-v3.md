---
UID: NS.winsplp._SPLCLIENT_INFO_2_V3
title: SPLCLIENT_INFO_2_V3
author: windows-driver-content
description: TBD.
old-location: print\splclient_info_2_longhorn.htm
ms.assetid: D058EF0A-014A-4A91-A8B5-6D4ACB1667E0
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SPLCLIENT_INFO_2_LONGHORN
req.alt-loc: Winsplp.h
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
ms.keywords: SPLCLIENT_INFO_2_V3, SPLCLIENT_INFO_2_LONGHORN
req.iface: 
req.product: Windows 10 or later.
---

# SPLCLIENT_INFO_2_V3 structure



## -description
<p>TBD</p>


## -syntax

````
typedef struct _SPLCLIENT_INFO_2_V3 {
  UINT64           hSplPrinter;
} SPLCLIENT_INFO_2_LONGHORN;
````


## -struct-fields
<dl>

### -field <b>hSplPrinter</b>

<dd>
<p>Specifies the server-side handle to be used for direct calls.</p>
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
<dt>Winsplp.h</dt>
</dl>
</td>
</tr>
</table>
---
UID: NS.rilapitypes.RILSTARTDTMFPARAMS
title: RILSTARTDTMFPARAMS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilstartdtmfparams_2.htm
ms.assetid: 51f6ea96-412a-429f-993b-de31f77f4d30
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILSTARTDTMFPARAMS
req.alt-loc: rilapitypes.h
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
ms.keywords: RILSTARTDTMFPARAMS, RILSTARTDTMFPARAMS
req.iface: 
req.product: Windows 10 or later.
---

# RILSTARTDTMFPARAMS structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILSTARTDTMFPARAMS {
  DWORD  dwExecutor;
  char   ch;
} RILSTARTDTMFPARAMS, RILSTARTDTMFPARAMS;
````


## -struct-fields
<dl>

### -field <b>dwExecutor</b>

<dd></dd>

### -field <b>ch</b>

<dd></dd>
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
<dt>Rilapitypes.h</dt>
</dl>
</td>
</tr>
</table>
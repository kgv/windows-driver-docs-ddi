---
UID: NS.rilapitypes.RILDELETEMSGPARAMS
title: RILDELETEMSGPARAMS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rildeletemsgparams_2.htm
ms.assetid: 793e9724-fff0-4bdc-a8ed-1e62fa54b4df
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
req.alt-api: RILDELETEMSGPARAMS
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
ms.keywords: RILDELETEMSGPARAMS, RILDELETEMSGPARAMS
req.iface: 
req.product: Windows 10 or later.
---

# RILDELETEMSGPARAMS structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILDELETEMSGPARAMS {
  HUICCAPP  hUiccApp;
  DWORD     dwIndex;
} RILDELETEMSGPARAMS, RILDELETEMSGPARAMS;
````


## -struct-fields
<dl>

### -field <b>hUiccApp</b>

<dd></dd>

### -field <b>dwIndex</b>

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
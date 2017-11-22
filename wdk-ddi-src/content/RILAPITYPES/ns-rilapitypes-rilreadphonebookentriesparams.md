---
UID: NS.rilapitypes.RILREADPHONEBOOKENTRIESPARAMS
title: RILREADPHONEBOOKENTRIESPARAMS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilreadphonebookentriesparams_2.htm
ms.assetid: 4cf1b9ab-0082-4ad3-9fd5-a29b51ca6bc0
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
req.alt-api: RILREADPHONEBOOKENTRIESPARAMS
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
ms.keywords: RILREADPHONEBOOKENTRIESPARAMS, RILREADPHONEBOOKENTRIESPARAMS
req.iface: 
req.product: Windows 10 or later.
---

# RILREADPHONEBOOKENTRIESPARAMS structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILREADPHONEBOOKENTRIESPARAMS {
  HUICCAPP                    hUiccApp;
  RILPHONEENTRYSTORELOCATION  dwStoreLocation;
  DWORD                       dwStartIndex;
  DWORD                       dwEndIndex;
} RILREADPHONEBOOKENTRIESPARAMS, RILREADPHONEBOOKENTRIESPARAMS;
````


## -struct-fields
<dl>

### -field <b>hUiccApp</b>

<dd></dd>

### -field <b>dwStoreLocation</b>

<dd></dd>

### -field <b>dwStartIndex</b>

<dd></dd>

### -field <b>dwEndIndex</b>

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
---
UID: NE.rilapitypes.RILIMSSUBSCRIBETYPE
title: RILIMSSUBSCRIBETYPE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilimssubscribetype_2.htm
ms.assetid: 84b2de56-55f9-471c-8d32-84fe1365dfbf
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILIMSSUBSCRIBETYPE
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
ms.keywords: RIL_WritePhonebookEntry
req.iface: 
req.product: Windows 10 or later.
---

# RILIMSSUBSCRIBETYPE enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef enum _RILIMSSUBSCRIBETYPE { 
  RIL_IMSSUBSCRIBETYPE_MWI,
  RIL_IMSSUBSCRIBETYPE_CONFERENCE,
  RIL_IMSSUBSCRIBETYPE_MAX
} RILIMSSUBSCRIBETYPE;
````


## -enum-fields
<dl>

### -field <a id="RIL_IMSSUBSCRIBETYPE_MWI"></a><a id="ril_imssubscribetype_mwi"></a><b>RIL_IMSSUBSCRIBETYPE_MWI</b>

<dd></dd>

### -field <a id="RIL_IMSSUBSCRIBETYPE_CONFERENCE"></a><a id="ril_imssubscribetype_conference"></a><b>RIL_IMSSUBSCRIBETYPE_CONFERENCE</b>

<dd></dd>

### -field <a id="RIL_IMSSUBSCRIBETYPE_MAX"></a><a id="ril_imssubscribetype_max"></a><b>RIL_IMSSUBSCRIBETYPE_MAX</b>

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
---
UID: NS.ntddrilapitypes.RILEXCHANGEUICCAPDUPARAMS
title: RILEXCHANGEUICCAPDUPARAMS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilexchangeuiccapduparams.htm
ms.assetid: be77f9e2-acf7-4b59-9a46-abda7c43817b
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddrilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILEXCHANGEUICCAPDUPARAMS
req.alt-loc: ntddrilapitypes.h
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
ms.keywords: RILEXCHANGEUICCAPDUPARAMS, RILEXCHANGEUICCAPDUPARAMS, *LPRILEXCHANGEUICCAPDUPARAMS
req.iface: 
---

# RILEXCHANGEUICCAPDUPARAMS structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILEXCHANGEUICCAPDUPARAMS {
  DWORD    dwSlotIndex;
  DWORD    dwChannelId;
  DWORD    dwAPDULength;
  BYTE [1] bAPDU;
} RILEXCHANGEUICCAPDUPARAMS, RILEXCHANGEUICCAPDUPARAMS;
````


## -struct-fields
<dl>

### -field <b>dwSlotIndex</b>

<dd></dd>

### -field <b>dwChannelId</b>

<dd></dd>

### -field <b>dwAPDULength</b>

<dd></dd>

### -field <b>bAPDU</b>

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
<dt>Ntddrilapitypes.h</dt>
</dl>
</td>
</tr>
</table>
---
UID: NS.ntddrilapitypes.RILADDITIONALNUMBERSTRINGUPDATE
title: RILADDITIONALNUMBERSTRINGUPDATE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\riladditionalnumberstringupdate.htm
ms.assetid: 43fe1e25-be15-4f7a-8ecf-e4492235c6c2
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
req.alt-api: RILADDITIONALNUMBERSTRINGUPDATE
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
ms.keywords: RILADDITIONALNUMBERSTRINGUPDATE, RILADDITIONALNUMBERSTRINGUPDATE, *LPRILADDITIONALNUMBERSTRINGUPDATE
req.iface: 
---

# RILADDITIONALNUMBERSTRINGUPDATE structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILADDITIONALNUMBERSTRINGUPDATE {
  DWORD                     cbSize;
  HUICCAPP                  hUiccApp;
  RILPHONEBOOKANSOPERATION  dwOpType;
  DWORD                     dwNumId;
  WCHAR [256]               wszText;
} RILADDITIONALNUMBERSTRINGUPDATE, RILADDITIONALNUMBERSTRINGUPDATE;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>hUiccApp</b>

<dd></dd>

### -field <b>dwOpType</b>

<dd></dd>

### -field <b>dwNumId</b>

<dd></dd>

### -field <b>wszText</b>

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
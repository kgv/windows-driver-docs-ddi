---
UID: NS.rilapitypes.RILMSGMWIDETAIL
title: RILMSGMWIDETAIL
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilmsgmwidetail_2.htm
ms.assetid: 58b0c3bc-f63a-4db7-a5e1-767f12b7655a
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
req.alt-api: RILMSGMWIDETAIL
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
ms.keywords: RILMSGMWIDETAIL, RILMSGMWIDETAIL
req.iface: 
req.product: Windows 10 or later.
---

# RILMSGMWIDETAIL structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILMSGMWIDETAIL {
  RILMSGMWITYPE                dwMwiType;
  RILMSGMWIPRIORITY            dwMwiPriority;
  RILADDRESS                   raToAddress;
  RILADDRESS                   raFromAddress;
  RILSYSTEMTIME                stDateSent;
  WCHAR [MAXLENGTH_MWISUBJECT] wszSubject;
  WCHAR [MAXLENGTH_ADDRESS]    wszMessageId;
} RILMSGMWIDETAIL, RILMSGMWIDETAIL;
````


## -struct-fields
<dl>

### -field <b>dwMwiType</b>

<dd></dd>

### -field <b>dwMwiPriority</b>

<dd></dd>

### -field <b>raToAddress</b>

<dd></dd>

### -field <b>raFromAddress</b>

<dd></dd>

### -field <b>stDateSent</b>

<dd></dd>

### -field <b>wszSubject</b>

<dd></dd>

### -field <b>wszMessageId</b>

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
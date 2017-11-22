---
UID: NS.bdatypes._BDA_CAS_REQUESTTUNERDATA
title: BDA_CAS_REQUESTTUNERDATA
author: windows-driver-content
description: TBD.
old-location: stream\bda_cas_requesttunerdata.htm
ms.assetid: 09347A56-C3F8-4E0D-A557-CECB7BBC7DB8
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: bdatypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BDA_CAS_REQUESTTUNERDATA
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
req.irql: PASSIVE_LEVEL
ms.keywords: BDA_CAS_REQUESTTUNERDATA, BDA_CAS_REQUESTTUNERDATA, *PBDA_CAS_REQUESTTUNERDATA
req.iface: 
---

# BDA_CAS_REQUESTTUNERDATA structure



## -description
<p>TBD</p>


## -syntax

````
typedef struct _BDA_CAS_REQUESTTUNERDATA {
  UCHAR ucRequestPriority;
  UCHAR ucRequestReason;
  UCHAR ucRequestConsequences;
  ULONG ulEstimatedTime;
} BDA_CAS_REQUESTTUNERDATA, *PBDA_CAS_REQUESTTUNERDATA;
````


## -struct-fields
<dl>

### -field <b>ucRequestPriority</b>

<dd>
<p>TBD</p>
</dd>

### -field <b>ucRequestReason</b>

<dd>
<p>TBD</p>
</dd>

### -field <b>ucRequestConsequences</b>

<dd>
<p>TBD</p>
</dd>

### -field <b>ulEstimatedTime</b>

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
<dt>Bdatypes.h</dt>
</dl>
</td>
</tr>
</table>
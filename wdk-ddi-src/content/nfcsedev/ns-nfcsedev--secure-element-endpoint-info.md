---
UID: NS.nfcsedev._SECURE_ELEMENT_ENDPOINT_INFO
title: SECURE_ELEMENT_ENDPOINT_INFO
author: windows-driver-content
description: SECURE_ELEMENT_ENDPOINT_INFO is a member of SECURE_ELEMENT_ENDPOINT_LIST.
old-location: nfpdrivers\_secure_element_endpoint_info.htm
ms.assetid: C1D812BD-55F0-44F7-BCC8-81CC758EDEF3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: nfpdrivers
req.header: nfcsedev.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SECURE_ELEMENT_ENDPOINT_INFO
req.alt-loc: nfcsedev.h
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
ms.keywords: SECURE_ELEMENT_ENDPOINT_INFO, SECURE_ELEMENT_ENDPOINT_INFO, *PSECURE_ELEMENT_ENDPOINT_INFO
req.iface: 
---

# SECURE_ELEMENT_ENDPOINT_INFO structure



## -description
<p>SECURE_ELEMENT_ENDPOINT_INFO is a member of <a href="https://msdn.microsoft.com/library/windows/hardware/dn905622">SECURE_ELEMENT_ENDPOINT_LIST</a>.</p>


## -syntax

````
typedef struct _SECURE_ELEMENT_ENDPOINT_INFO {
  GUID                guidSecureElementId;
  SECURE_ELEMENT_TYPE eSecureElementType;
} SECURE_ELEMENT_ENDPOINT_INFO, *P_SECURE_ELEMENT_ENDPOINT_INFO;
````


## -struct-fields
<dl>

### -field <b>guidSecureElementId</b>

<dd>
<p>This is a unique identifier for the secure element.</p>
</dd>

### -field <b>eSecureElementType</b>

<dd>
<p>Type of secure element endpoint (NFCEE).</p>
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
<dt>Nfcsedev.h</dt>
</dl>
</td>
</tr>
</table>
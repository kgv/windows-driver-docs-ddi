---
UID: NE.rilapitypes.RILUICCRESPONSEPARAMMASK
title: RILUICCRESPONSEPARAMMASK
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\riluiccresponseparammask_2.htm
ms.assetid: b281375a-a2bf-4b19-af94-a3902cf462b2
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
req.alt-api: RILUICCRESPONSEPARAMMASK
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

# RILUICCRESPONSEPARAMMASK enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef enum _RILUICCRESPONSEPARAMMASK { 
  RIL_PARAM_SR_STATUSWORD2,
  RIL_PARAM_SR_RESPONSESIZE,
  RIL_PARAM_SR_RESPONSE,
  RIL_PARAM_SR_ALL
} RILUICCRESPONSEPARAMMASK;
````


## -enum-fields
<dl>

### -field <a id="RIL_PARAM_SR_STATUSWORD2"></a><a id="ril_param_sr_statusword2"></a><b>RIL_PARAM_SR_STATUSWORD2</b>

<dd></dd>

### -field <a id="RIL_PARAM_SR_RESPONSESIZE"></a><a id="ril_param_sr_responsesize"></a><b>RIL_PARAM_SR_RESPONSESIZE</b>

<dd></dd>

### -field <a id="RIL_PARAM_SR_RESPONSE"></a><a id="ril_param_sr_response"></a><b>RIL_PARAM_SR_RESPONSE</b>

<dd></dd>

### -field <a id="RIL_PARAM_SR_ALL"></a><a id="ril_param_sr_all"></a><b>RIL_PARAM_SR_ALL</b>

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
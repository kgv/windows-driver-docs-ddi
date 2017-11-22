---
UID: NE.ntddrilapitypes.RILDIALEDIDSETTINGSPARAMMASK
title: RILDIALEDIDSETTINGSPARAMMASK
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rildialedidsettingsparammask.htm
ms.assetid: 8883e9fc-9f2a-4367-ae2d-30260f2d2de6
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddrilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILDIALEDIDSETTINGSPARAMMASK
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
ms.keywords: TUPLE_REQUEST, TUPLE_REQUEST, *PTUPLE_REQUEST
req.iface: 
---

# RILDIALEDIDSETTINGSPARAMMASK enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef enum _RILDIALEDIDSETTINGSPARAMMASK { 
  RIL_PARAM_DIDS_PROVISIONING,
  RIL_PARAM_DIDS_STATUS,
  RIL_PARAM_DIDS_ALL
} RILDIALEDIDSETTINGSPARAMMASK;
````


## -enum-fields
<dl>

### -field <a id="RIL_PARAM_DIDS_PROVISIONING"></a><a id="ril_param_dids_provisioning"></a><b>RIL_PARAM_DIDS_PROVISIONING</b>

<dd></dd>

### -field <a id="RIL_PARAM_DIDS_STATUS"></a><a id="ril_param_dids_status"></a><b>RIL_PARAM_DIDS_STATUS</b>

<dd></dd>

### -field <a id="RIL_PARAM_DIDS_ALL"></a><a id="ril_param_dids_all"></a><b>RIL_PARAM_DIDS_ALL</b>

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
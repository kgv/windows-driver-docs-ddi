---
UID: NE.ntddrilapitypes.RILMSGOUTSUBMITVPFORMAT
title: RILMSGOUTSUBMITVPFORMAT
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilmsgoutsubmitvpformat.htm
ms.assetid: c0a2646c-aa0a-4946-999f-a78d1c488752
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
req.alt-api: RILMSGOUTSUBMITVPFORMAT
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

# RILMSGOUTSUBMITVPFORMAT enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef enum _RILMSGOUTSUBMITVPFORMAT { 
  RIL_MSGVP_RELATIVE,
  RIL_MSGVP_ENHANCED,
  RIL_MSGVP_ABSOLUTE,
  RIL_MSGVP_MAX
} RILMSGOUTSUBMITVPFORMAT;
````


## -enum-fields
<dl>

### -field <a id="RIL_MSGVP_RELATIVE"></a><a id="ril_msgvp_relative"></a><b>RIL_MSGVP_RELATIVE</b>

<dd></dd>

### -field <a id="RIL_MSGVP_ENHANCED"></a><a id="ril_msgvp_enhanced"></a><b>RIL_MSGVP_ENHANCED</b>

<dd></dd>

### -field <a id="RIL_MSGVP_ABSOLUTE"></a><a id="ril_msgvp_absolute"></a><b>RIL_MSGVP_ABSOLUTE</b>

<dd></dd>

### -field <a id="RIL_MSGVP_MAX"></a><a id="ril_msgvp_max"></a><b>RIL_MSGVP_MAX</b>

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
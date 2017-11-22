---
UID: NE.ntddrilapitypes.RILCALLINFOFLAGS
title: RILCALLINFOFLAGS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilcallinfoflags.htm
ms.assetid: c4edec8f-a001-491b-a3e6-03d19ac94f18
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
req.alt-api: RILCALLINFOFLAGS
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

# RILCALLINFOFLAGS enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef enum _RILCALLINFOFLAGS { 
  RILCALLINFO_FLAG_ALIENCALL,
  RILCALLINFO_FLAG_EMERGENCYCALL
} RILCALLINFOFLAGS;
````


## -enum-fields
<dl>

### -field <a id="RILCALLINFO_FLAG_ALIENCALL"></a><a id="rilcallinfo_flag_aliencall"></a><b>RILCALLINFO_FLAG_ALIENCALL</b>

<dd></dd>

### -field <a id="RILCALLINFO_FLAG_EMERGENCYCALL"></a><a id="rilcallinfo_flag_emergencycall"></a><b>RILCALLINFO_FLAG_EMERGENCYCALL</b>

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
---
UID: NS.ntddrilapitypes.RILCALLHANDOVERSTATE
title: RILCALLHANDOVERSTATE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilcallhandoverstate.htm
ms.assetid: 1c9fb343-32f1-444e-9328-097da72cd006
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
req.alt-api: RILCALLHANDOVERSTATE
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
ms.keywords: RILCALLHANDOVERSTATE, RILCALLHANDOVERSTATE, *LPRILCALLHANDOVERSTATE
req.iface: 
---

# RILCALLHANDOVERSTATE structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILCALLHANDOVERSTATE {
  DWORD                 cbSize;
  DWORD                 dwParams;
  RILCALLHANDOVERPHASE  dwPhase;
  RILCALLTYPE           dwOldType;
  RILCALLTYPE           dwNewType;
  DWORD                 dw3gppCause;
} RILCALLHANDOVERSTATE, RILCALLHANDOVERSTATE;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwPhase</b>

<dd></dd>

### -field <b>dwOldType</b>

<dd></dd>

### -field <b>dwNewType</b>

<dd></dd>

### -field <b>dw3gppCause</b>

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
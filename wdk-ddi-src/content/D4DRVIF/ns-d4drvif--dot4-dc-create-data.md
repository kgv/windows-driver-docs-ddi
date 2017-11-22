---
UID: NS.d4drvif._DOT4_DC_CREATE_DATA
title: DOT4_DC_CREATE_DATA
author: windows-driver-content
description: Defines the DOT4_DC_CREATE_DATA construct.
old-location: print\dot4_dc_create_data.htm
ms.assetid: 9C21732B-0AB1-4F3E-8F3D-F0B12007920A
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: d4drvif.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DOT4_DC_CREATE_DATA
req.alt-loc: D4drvif.h
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
ms.keywords: DOT4_DC_CREATE_DATA, DOT4_DC_CREATE_DATA, *PDOT4_DC_CREATE_DATA
req.iface: 
---

# DOT4_DC_CREATE_DATA structure



## -description
<p>Defines the <b>DOT4_DC_CREATE_DATA</b> construct.</p>


## -syntax

````
typedef struct _DOT4_DC_CREATE_DATA {
  unsigned char bPsid;
  CHAR          pServiceName[MAX_SERVICE_LENGTH + 1];
  unsigned char bType;
  ULONG         ulBufferSize;
  USHORT        usMaxHtoPPacketSize;
  USHORT        usMaxPtoHPacketSize;
  unsigned char bHsid;
} DOT4_DC_CREATE_DATA, *PDOT4_DC_CREATE_DATA;
````


## -struct-fields
<dl>

### -field <b>bPsid</b>

<dd>
<p>Specifies this or the service name sent.</p>
</dd>

### -field <b>pServiceName</b>

<dd>
<p>Describes the <b>CHAR</b>  member <b>pServiceName</b>.</p>
</dd>

### -field <b>bType</b>

<dd>
<p>Specifies the type, stream or packet, of channels on the socket.</p>
</dd>

### -field <b>ulBufferSize</b>

<dd>
<p>Specifies the size of the read buffer for channels on socket.</p>
</dd>

### -field <b>usMaxHtoPPacketSize</b>

<dd>
<p>Describes the <b>USHORT</b> member <b>usMaxHtoPPacketSize</b>.</p>
</dd>

### -field <b>usMaxPtoHPacketSize</b>

<dd>
<p>Describes the <b>USHORT</b> member <b>usMaxPtoHPacketSize</b>.</p>
</dd>

### -field <b>bHsid</b>

<dd>
<p>Specifies the host socket ID returned.</p>
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
<dt>D4drvif.h</dt>
</dl>
</td>
</tr>
</table>
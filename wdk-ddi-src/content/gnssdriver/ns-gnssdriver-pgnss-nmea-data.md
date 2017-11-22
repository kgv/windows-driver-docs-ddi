---
UID: NS.gnssdriver.PGNSS_NMEA_DATA
title: PGNSS_NMEA_DATA
author: windows-driver-content
description: This structure contains generic (non-parsed) NMEA data.
old-location: sensors\gnss_nmea_data.htm
ms.assetid: 6B890F85-0E77-41D2-B3B9-004F1882B6B5
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: sensors
req.header: gnssdriver.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GNSS_NMEA_DATA
req.alt-loc: gnssdriver.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: PGNSS_NMEA_DATA, GNSS_NMEA_DATA, *PGNSS_NMEA_DATA
req.iface: 
---

# PGNSS_NMEA_DATA structure



## -description
<p>This structure contains generic (non-parsed) NMEA data.</p>


## -syntax

````
typedef struct {
  ULONG Size;
  ULONG Version;
  CHAR  NmeaSentences[256];
} GNSS_NMEA_DATA, *PGNSS_NMEA_DATA;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Structure size.</p>
</dd>

### -field <b>Version</b>

<dd>
<p>Version number.</p>
</dd>

### -field <b>NmeaSentences[256]</b>

<dd>
<p>Generic (non-parsed) NMEA data </p>
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
<dt>Gnssdriver.h</dt>
</dl>
</td>
</tr>
</table>
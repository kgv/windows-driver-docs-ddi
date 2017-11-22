---
UID: NS.gnssdriver.PGNSS_SUPL_HSLP_CONFIG
title: PGNSS_SUPL_HSLP_CONFIG
author: windows-driver-content
description: This structure contains SUPL H-SLP configuration information.
old-location: sensors\gnss_supl_hslp_config.htm
ms.assetid: 08CCC4A8-2D85-436D-B18E-77C91A24F59C
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
req.alt-api: GNSS_SUPL_HSLP_CONFIG
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
ms.keywords: PGNSS_SUPL_HSLP_CONFIG, GNSS_SUPL_HSLP_CONFIG, *PGNSS_SUPL_HSLP_CONFIG
req.iface: 
---

# PGNSS_SUPL_HSLP_CONFIG structure



## -description
<p>This structure contains SUPL H-SLP configuration information.</p>


## -syntax

````
typedef struct {
  ULONG Size;
  ULONG Version;
  WCHAR SuplHslp[MAX_SERVER_URL_NAME];
  WCHAR SuplHslpFromImsi[MAX_SERVER_URL_NAME];
  ULONG Reserved;
  BYTE  Unused[512];
} GNSS_SUPL_HSLP_CONFIG, *PGNSS_SUPL_HSLP_CONFIG;
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

### -field <b>SuplHslp[MAX_SERVER_URL_NAME]</b>

<dd>
<p>This is the SUPL server address with TCP port. The server address will be a FQDN as indicated in the OMA SUPL specs.</p>
</dd>

### -field <b>SuplHslpFromImsi[MAX_SERVER_URL_NAME]</b>

<dd>
<p>This is the SUPL server address as derived from IMSI.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>Unused[512]</b>

<dd>
<p>Padding buffer.</p>
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
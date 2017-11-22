---
UID: NS.wwan._WWAN_CDMA_MRL_INFO
title: WWAN_CDMA_MRL_INFO
author: windows-driver-content
description: The WWAN_CDMA_MRL_INFO structure represents information about a CDMA serving cell or neighboring cell.
old-location: netvista\wwan_cdma_mrl_info.htm
ms.assetid: D8633E80-C7A3-4050-8E8E-8AE459F905D5
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1709
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_CDMA_MRL_INFO
req.alt-loc: wwan.h
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
ms.keywords: WWAN_CDMA_MRL_INFO, WWAN_CDMA_MRL_INFO, *PWWAN_CDMA_MRL_INFO
req.iface: 
req.product: Windows 10 or later.
---

# WWAN_CDMA_MRL_INFO structure



## -description
<p>The <b>WWAN_CDMA_MRL_INFO</b> structure represents information about a CDMA serving cell or neighboring cell.</p>


## -syntax

````
typedef struct _WWAN_CDMA_MRL_INFO {
  ULONG ServingCellFlag;
  ULONG NID;
  ULONG SID;
  ULONG BaseStationId;
  ULONG BaseLatitude;
  ULONG BaseLongitude;
  ULONG RefPn;
  ULONG GPSSeconds;
  ULONG PilotStrength;
} WWAN_CDMA_MRL_INFO, *PWWAN_CDMA_MRL_INFO;
````


## -struct-fields
<dl>

### -field <b>ServingCellFlag</b>

<dd>
<p>Indicates whether this is a serving cell. A value of 1 indicates a serving cell, while a value of 0 indicates a neighboring cell. There may be more than one serving cell at a time (notably while in a call).</p>
</dd>

### -field <b>NID</b>

<dd>
<p>The Network ID (0-65535). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>SID</b>

<dd>
<p>The System ID (0-32767). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>BaseStationId</b>

<dd>
<p>The Base Station ID (0-65535). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>BaseLatitude</b>

<dd>
<p>The Base Station Latitude (0-4194303). This is encoded in units of 0.25 seconds, expressed in two’s complement representation within the low 22 bits of the DWORD. As a signed value, North latitudes are positive. Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>BaseLongitude</b>

<dd>
<p>The Base Station Longitude (0-8388607). This is encoded in units of 0.25 seconds, expressed in two’s complement representation within the low 23 bits of the DWORD. As a signed value, East longitudes are positive. Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>RefPn</b>

<dd>
<p>The Base Station PN Number (0-511). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>GPSSeconds</b>

<dd>
<p>The GPS seconds, or the time at which this arrived from the base station. Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>PilotStrength</b>

<dd>
<p>The Signal Strength of the pilot (0-63). Use 0xFFFFFFFF when this information is not available.</p>
</dd>
</dl>

## -remarks
<p><b>WWAN_CDMA_MRL_INFO</b> is designed for the CDMA2000 network type. There can be more than one CDMA2000 serving cell at the same time. Both serving cells and neighboring cells will be returned in the same list. The <b>ServingCellFlag</b> member indicates whether a cell is a serving cell or not.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Windows 10, version 1709</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wwan.h (include Wwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/66460B28-C2B4-4F05-A133-31A753AF9489">WWAN_BASE_STATIONS_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/A19B98B5-F2E5-4AF9-9D2B-A7DD47441656">WWAN_CDMA_MRL</a>
</dt>
<dt>
<a href="https://docs.microsoft.com/windows-hardware/drivers/network/mb-base-stations-information-query-support">MB base stations information query support</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WWAN_CDMA_MRL_INFO structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
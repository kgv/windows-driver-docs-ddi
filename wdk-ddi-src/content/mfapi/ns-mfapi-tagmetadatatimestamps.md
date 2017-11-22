---
UID: NS.mfapi.tagMetadataTimeStamps
title: tagMetadataTimeStamps
author: windows-driver-content
description: The MetadataTimeStamps structure describes the blob format for the MF_CAPTURE_METADATA_FACEROITIMESTAMPS attribute.
old-location: stream\metadatatimestamps.htm
ms.assetid: F7E5349B-37F0-4B94-B42B-EAEB04DC1AB5
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: mfapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MetadataTimeStamps
req.alt-loc: mfapi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: tagMetadataTimeStamps, MetadataTimeStamps
req.iface: 
---

# tagMetadataTimeStamps structure



## -description
<p>The <b>MetadataTimeStamps</b> structure describes the blob format for the <b>MF_CAPTURE_METADATA_FACEROITIMESTAMPS</b> attribute.</p>


## -syntax

````
typedef struct tagMetadataTimeStamps {
  ULONG    Flags;
  LONGLONG Device;
  LONGLONG Presentation;
} MetadataTimeStamps;
````


## -struct-fields
<dl>

### -field <b>Flags</b>

<dd>
<p>Bitwise OR of the <b>MF_METADATATIMESTAMPS_*</b> flags.</p>
</dd>

### -field <b>Device</b>

<dd>
<p>QPC time for the sample  the face rectangle is derived from (in 100ns).</p>
</dd>

### -field <b>Presentation</b>

<dd>
<p>PTS for the sample  the face rectangle is derived from (in 100ns).</p>
</dd>
</dl>

## -remarks
<p>The <b>MF_CAPTURE_METADATA_FACEROITIMESTAMPS</b> attribute contains the time stamp information for the face ROIs identified in <b>MF_CAPTURE_METADATA_FACEROIS</b>.  For a  device that cannot provide the time stamp for face ROIs, this attribute should be omitted.</p>

<p>For the <b>Flags</b> field, the following bit flags  indicate which time stamp is valid:<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>#define MF_METADATATIMESTAMPS_DEVICE        0x00000001
#define MF_METADATATIMESTAMPS_PRESENTATION  0x00000002</pre>
</td>
</tr>
</table></span></div>
</p>

<p>MFT0 must set <b>Flags</b> to <b>MF_METADATATIEMSTAMPS_DEVICE</b> and the appropriate QPC time for <b>Device</b>, if the driver provides the timestamp metadata for the face ROIs.</p>

<p>The <b>MetadataTimeStamps</b> structure only describes the blob format for the <b>MF_CAPTURE_METADATA_FACEROITIMESTAMPS</b> attribute.  The metadata item structure for timestamp (<a href="https://msdn.microsoft.com/library/windows/hardware/dn925184">KSCAMERA_METADATA_ITEMHEADER</a> + timestamp metadata payload) is up to driver and must be 8-byte aligned.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Mfapi.h</dt>
</dl>
</td>
</tr>
</table>
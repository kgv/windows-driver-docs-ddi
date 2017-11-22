---
UID: NS.ks.PKSSTREAM_METADATA_INFO
title: PKSSTREAM_METADATA_INFO
author: windows-driver-content
description: This structure contains the metadata information that is passed down to the driver.
old-location: stream\ksstream_metadata_info.htm
ms.assetid: 40C09BCD-407F-4F2D-8780-4DEC1C9246E8
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSSTREAM_METADATA_INFO
req.alt-loc: Ks.h
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
ms.keywords: PKSSTREAM_METADATA_INFO, KSSTREAM_METADATA_INFO, *PKSSTREAM_METADATA_INFO
req.iface: 
---

# PKSSTREAM_METADATA_INFO structure



## -description
<p>This structure contains the metadata information that is passed down to the driver.</p>


## -syntax

````
typedef struct {
  ULONG                               BufferSize;
  ULONG                               UsedSize;
  Field_size_bytes_(BufferSize) PVOID Data;
  Field_size_bytes_(BufferSize) PVOID SystemVa;
  ULONG                               Flags;
  ULONG                               Reserved;
} KSSTREAM_METADATA_INFO, *PKSSTREAM_METADATA_INFO;
````


## -struct-fields
<dl>

### -field <b>BufferSize</b>

<dd>
<p>This value is set by the user mode component and is equal to the MaxMetadataBufferSize supplied by the driver.</p>
</dd>

### -field <b>UsedSize</b>

<dd>
<p>The size of the metadata written by the driver in the SystemVa buffer.</p>
</dd>

### -field <b>Data</b>

<dd>
<p>The metadata buffer that is passed down by the user mode component. This is mapped to <i>SystemVa</i>.</p>
</dd>

### -field <b>SystemVa</b>

<dd>
<p>The buffer that is used by the driver to fill with metadata.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Set to KSCAMERA_EXTENDEDPROP_METADATA_SYSTEMMEMORY if the metadata buffer is allocated from the system memory.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved for system use.</p>
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
<dt>Ks.h</dt>
</dl>
</td>
</tr>
</table>
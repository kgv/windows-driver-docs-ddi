---
UID: NE.portcls._PcStreamResourceType
title: PcStreamResourceType
author: windows-driver-content
description: This topic discusses the PcStreamResourceType enum, and describes its members. The PcStreamResourceType enum is used to define the type of resources used for specific audio streaming.
old-location: audio\pcstreamresourcetype.htm
ms.assetid: C9563635-66F3-4835-8153-DECB04580544
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: audio
req.header: portcls.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcStreamResourceType, *PPcStreamResourceType
req.alt-loc: Portcls.h
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
ms.keywords: BarcodeSymbologyAttributesData, BarcodeSymbologyAttributesData
req.iface: 
---

# PcStreamResourceType enumeration



## -description
<p>This topic discusses the PcStreamResourceType enum, and describes its members. The PcStreamResourceType enum is used to define the type of resources used for specific audio streaming </p>


## -syntax

````
typedef enum PcStreamResourceType { 
  ePcStreamResourceInterrupt,
  ePcStreamResourceThread,
  ePcStreamResourceSet
} PcStreamResourceType, *PPcStreamResourceType;
````


## -enum-fields
<dl>

### -field <a id="ePcStreamResourceInterrupt"></a><a id="epcstreamresourceinterrupt"></a><a id="EPCSTREAMRESOURCEINTERRUPT"></a><b>ePcStreamResourceInterrupt</b>

<dd>
<p>The resource is a PKINTERRUPT. </p>
</dd>

### -field <a id="ePcStreamResourceThread"></a><a id="epcstreamresourcethread"></a><a id="EPCSTREAMRESOURCETHREAD"></a><b>ePcStreamResourceThread</b>

<dd>
<p> The resource is a PETHREAD. </p>
</dd>

### -field <a id="ePcStreamResourceSet"></a><a id="epcstreamresourceset"></a><a id="EPCSTREAMRESOURCESET"></a><b>ePcStreamResourceSet</b>

<dd>
<p>The resource is a link to another device-stack’s resources. </p>
</dd>
</dl>

## -remarks
<p>Stream resources are any resources used by the audio driver to process audio streams or ensure audio data flow. Two type of stream resources are supported: interrupts and driver-owned threads. Audio drivers should register a resource after creating the resource, and unregister the resource before deleted it. 
</p>

<p>Stream resources are any resources used by the audio driver to process audio streams or ensure audio data flow. Two type of stream resources are supported: interrupts and driver-owned threads. Audio drivers should register a resource after creating the resource, and unregister the resource before deleted it. 
</p>

<p>Stream resources are any resources used by the audio driver to process audio streams or ensure audio data flow. Two type of stream resources are supported: interrupts and driver-owned threads. Audio drivers should register a resource after creating the resource, and unregister the resource before deleted it. 
</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Portcls.h</dt>
</dl>
</td>
</tr>
</table>
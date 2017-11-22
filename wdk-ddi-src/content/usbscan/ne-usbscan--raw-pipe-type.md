---
UID: NE.usbscan._RAW_PIPE_TYPE
title: RAW_PIPE_TYPE
author: windows-driver-content
description: The RAW_PIPE_TYPE data type is used to specify the type of a USB pipe.
old-location: image\raw_pipe_type.htm
ms.assetid: 6af4161c-7caa-4d80-8938-303380ee3058
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: image
req.header: usbscan.h
req.include-header: Usbscan.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RAW_PIPE_TYPE
req.alt-loc: usbscan.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: USB_TRANSPORT_CHARACTERISTICS, USB_TRANSPORT_CHARACTERISTICS, *PUSB_TRANSPORT_CHARACTERISTICS
req.iface: 
req.product: Windows 10 or later.
---

# RAW_PIPE_TYPE enumeration



## -description
<p>The RAW_PIPE_TYPE data type is used to specify the type of a USB pipe. The values are defined as follows:</p>


## -syntax

````
typedef enum _RAW_PIPE_TYPE { 
  USBSCAN_PIPE_CONTROL      = 0,
  USBSCAN_PIPE_ISOCHRONOUS  = 1,
  USBSCAN_PIPE_BULK         = 2,
  USBSCAN_PIPE_INTERRUPT    = 3
} RAW_PIPE_TYPE;
````


## -enum-fields
<dl>

### -field <a id="USBSCAN_PIPE_CONTROL"></a><a id="usbscan_pipe_control"></a><b>USBSCAN_PIPE_CONTROL</b>

<dd>
<p>Identifies the control pipe.</p>
</dd>

### -field <a id="USBSCAN_PIPE_ISOCHRONOUS"></a><a id="usbscan_pipe_isochronous"></a><b>USBSCAN_PIPE_ISOCHRONOUS</b>

<dd>
<p>Identifies an isochronous pipe.</p>
</dd>

### -field <a id="USBSCAN_PIPE_BULK"></a><a id="usbscan_pipe_bulk"></a><b>USBSCAN_PIPE_BULK</b>

<dd>
<p>Identifies a bulk IN or bulk OUT pipe.</p>
</dd>

### -field <a id="USBSCAN_PIPE_INTERRUPT"></a><a id="usbscan_pipe_interrupt"></a><b>USBSCAN_PIPE_INTERRUPT</b>

<dd>
<p>Identifies an interrupt pipe.</p>
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
<dt>Usbscan.h (include Usbscan.h)</dt>
</dl>
</td>
</tr>
</table>
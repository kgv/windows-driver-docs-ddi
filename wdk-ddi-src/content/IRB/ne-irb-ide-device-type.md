---
UID: NE.irb.IDE_DEVICE_TYPE
title: IDE_DEVICE_TYPE
author: windows-driver-content
description: The IDE_DEVICE_TYPE enumeration type indicates the device type.Note  The ATA port driver and ATA miniport driver models may be altered or unavailable in the future.
old-location: storage\ide_device_type.htm
ms.assetid: 6d94189f-d6ab-40ad-85e5-f4efe8c30ed8
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: Storage
req.header: irb.h
req.include-header: Irb.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDE_DEVICE_TYPE
req.alt-loc: irb.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level
ms.keywords: WdmlibIoGetAffinityInterrupt
req.iface: 
---

# IDE_DEVICE_TYPE enumeration



## -description
<p>The IDE_DEVICE_TYPE enumeration type indicates the device type.</p>


## -syntax

````
typedef enum  { 
  DeviceUnknown   = 0,
  DeviceIsAta     = 1,
  DeviceIsAtapi   = 2,
  DeviceNotExist  = 3
} IDE_DEVICE_TYPE;
````


## -enum-fields
<dl>

### -field <a id="DeviceUnknown"></a><a id="deviceunknown"></a><a id="DEVICEUNKNOWN"></a><b>DeviceUnknown</b>

<dd>
<p>Indicates that the device does not communicate by means of a known protocol.</p>
</dd>

### -field <a id="DeviceIsAta"></a><a id="deviceisata"></a><a id="DEVICEISATA"></a><b>DeviceIsAta</b>

<dd>
<p>Indicates an ATA device.</p>
</dd>

### -field <a id="DeviceIsAtapi"></a><a id="deviceisatapi"></a><a id="DEVICEISATAPI"></a><b>DeviceIsAtapi</b>

<dd>
<p>Indicates an ATAPI device.</p>
</dd>

### -field <a id="DeviceNotExist"></a><a id="devicenotexist"></a><a id="DEVICENOTEXIST"></a><b>DeviceNotExist</b>

<dd>
<p>Indicates that the device does not exist.</p>
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
<dt>Irb.h (include Irb.h)</dt>
</dl>
</td>
</tr>
</table>
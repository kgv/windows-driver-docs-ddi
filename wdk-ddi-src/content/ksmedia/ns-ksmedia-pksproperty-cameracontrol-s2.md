---
UID: NS.ksmedia.PKSPROPERTY_CAMERACONTROL_S2
title: PKSPROPERTY_CAMERACONTROL_S2
author: windows-driver-content
description: The KSPROPERTY_CAMERACONTROL_S2 structure describes filter-based properties in the PROPSETID_VIDCAP_CAMERACONTROL property set that use two values at the same time.
old-location: stream\ksproperty_cameracontrol_s2.htm
ms.assetid: b0ea25c0-5b10-403f-8c61-7840fe062596
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ksmedia.h
req.include-header: Ksmedia.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSPROPERTY_CAMERACONTROL_S2
req.alt-loc: ksmedia.h
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
ms.keywords: PKSPROPERTY_CAMERACONTROL_S2, KSPROPERTY_CAMERACONTROL_S2, *PKSPROPERTY_CAMERACONTROL_S2
req.iface: 
---

# PKSPROPERTY_CAMERACONTROL_S2 structure



## -description
<p>The KSPROPERTY_CAMERACONTROL_S2 structure describes filter-based properties in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567802">PROPSETID_VIDCAP_CAMERACONTROL</a> property set that use two values at the same time.</p>


## -syntax

````
typedef struct {
  KSPROPERTY Property;
  LONG       Value1;
  ULONG      Flags;
  ULONG      Capabilities;
  LONG       Value2;
} KSPROPERTY_CAMERACONTROL_S2, *PKSPROPERTY_CAMERACONTROL_S2;
````


## -struct-fields
<dl>

### -field <b>Property</b>

<dd>
<p>Specifies an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a> structure that describes the property set, property ID, and request type. </p>
</dd>

### -field <b>Value1</b>

<dd>
<p>Specifies the first value of the property. This member is read/write.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Indicates, for get requests, the current setting for the specified property from the values listed below. Indicates, for set requests, the desired setting for the specified property from the values listed below. This member can be set to one of the following values that are defined in <i>ksmedia.h</i>:</p>
<table>
<tr>
<th>Flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_MANUAL</p>
</td>
<td>
<p>Indicates that the setting is controlled manually</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_AUTO</p>
</td>
<td>
<p>Indicates that the setting is controlled automatically</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_ABSOLUTE</p>
</td>
<td>
<p>Indicates that the setting is in absolute values</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_RELATIVE</p>
</td>
<td>
<p>Indicates that the setting is in relative values</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>Capabilities</b>

<dd>
<p>Indicates the minidriver's camera control capabilities for the specified property. This member is read-only. This member can be set to one of the following values that are defined in <i>ksmedia.h</i>:</p>
<table>
<tr>
<th>Flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_MANUAL</p>
</td>
<td>
<p>Indicates that the device can be controlled manually</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_AUTO</p>
</td>
<td>
<p>Indicates that the device can be controlled automatically</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_ABSOLUTE</p>
</td>
<td>
<p>Indicates that the device settings are in absolute values</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_CAMERACONTROL_FLAGS_RELATIVE</p>
</td>
<td>
<p>Indicates that the device settings are in relative values</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>Value2</b>

<dd>
<p>Specifies the second value of the property. This member is read/write.</p>
</dd>
</dl>

## -remarks
<p>This structure is used by <a href="https://msdn.microsoft.com/library/windows/hardware/ff564425">KSPROPERTY_CAMERACONTROL_PANTILT</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff564427">KSPROPERTY_CAMERACONTROL_PANTILT_RELATIVE</a> for filter-based get/set property requests.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ksmedia.h (include Ksmedia.h)</dt>
</dl>
</td>
</tr>
</table>
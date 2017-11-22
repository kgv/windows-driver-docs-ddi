---
UID: NS.ks.PKSP_TIMEFORMAT
title: PKSP_TIMEFORMAT
author: windows-driver-content
description: The KSP_TIMEFORMAT structure corresponds to KSPROPERTY_MEDIASEEKING_CONVERTTIMEFORMAT.
old-location: stream\ksp_timeformat.htm
ms.assetid: 18ce5fc5-927c-4261-8966-bb12849b95c9
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSP_TIMEFORMAT
req.alt-loc: ks.h
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
ms.keywords: PKSP_TIMEFORMAT, KSP_TIMEFORMAT, *PKSP_TIMEFORMAT
req.iface: 
---

# PKSP_TIMEFORMAT structure



## -description
<p>The KSP_TIMEFORMAT structure corresponds to <a href="https://msdn.microsoft.com/library/windows/hardware/ff565181">KSPROPERTY_MEDIASEEKING_CONVERTTIMEFORMAT</a>.</p>


## -syntax

````
typedef struct {
  KSPROPERTY Property;
  GUID       SourceFormat;
  GUID       TargetFormat;
  LONGLONG   Time;
} KSP_TIMEFORMAT, *PKSP_TIMEFORMAT;
````


## -struct-fields
<dl>

### -field <b>Property</b>

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a> structure.</p>
</dd>

### -field <b>SourceFormat</b>

<dd>
<p>Pointer to a GUID that specifies the format to convert. If <b>NULL</b>, the current format is used.</p>
</dd>

### -field <b>TargetFormat</b>

<dd>
<p>Pointer to a GUID that specifies the target format. If <b>NULL</b>, the current format is used.</p>
</dd>

### -field <b>Time</b>

<dd>
<p>Specifies the time value to convert.</p>
</dd>
</dl>

## -remarks
<p>The fields of the structure correspond one to one with DirectShow's IMediaSeeking::ConvertTimeFormat.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565181">KSPROPERTY_MEDIASEEKING_CONVERTTIMEFORMAT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KSP_TIMEFORMAT structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
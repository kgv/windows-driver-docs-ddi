---
UID: NS.ks.PKSQUALITY_MANAGER
title: PKSQUALITY_MANAGER
author: windows-driver-content
description: The KSQUALITY_MANAGER structure is used with the KSPROPERTY_STREAM_QUALITY property and contains the handle of the quality manager sink and a context to pass in the quality complaints.
old-location: stream\ksquality_manager.htm
ms.assetid: 33e66fa0-53d6-400a-a03b-6d7b3fd01ace
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
req.alt-api: KSQUALITY_MANAGER
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
ms.keywords: PKSQUALITY_MANAGER, KSQUALITY_MANAGER, *PKSQUALITY_MANAGER
req.iface: 
---

# PKSQUALITY_MANAGER structure



## -description
<p>The KSQUALITY_MANAGER structure is used with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff565750">KSPROPERTY_STREAM_QUALITY</a> property and contains the handle of the quality manager sink and a context to pass in the quality complaints.</p>


## -syntax

````
typedef struct {
  HANDLE QualityManager;
  PVOID  Context;
} KSQUALITY_MANAGER, *PKSQUALITY_MANAGER;
````


## -struct-fields
<dl>

### -field <b>QualityManager</b>

<dd>
<p>Specifies a handle to the quality manager sink receiving the <a href="https://msdn.microsoft.com/library/windows/hardware/ff566728">KSQUALITY</a> complaint structures.</p>
</dd>

### -field <b>Context</b>

<dd>
<p>Specifies the context parameter to use when reporting quality problems. The context is used by the quality manager to distinguish between various clients that can send complaints to the same file object.</p>
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
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565750">KSPROPERTY_STREAM_QUALITY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566728">KSQUALITY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KSQUALITY_MANAGER structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
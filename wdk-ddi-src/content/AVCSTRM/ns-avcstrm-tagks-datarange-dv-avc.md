---
UID: NS.avcstrm.tagKS_DATARANGE_DV_AVC
title: tagKS_DATARANGE_DV_AVC
author: windows-driver-content
description: The KS_DATARANGE_DV_AVC structure stores a range of AV/C digital video formats.
old-location: stream\ks_datarange_dv_avc.htm
ms.assetid: 92759ba0-79f1-4dec-aea5-62c24253c6f0
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: avcstrm.h
req.include-header: Avcstrm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KS_DATARANGE_DV_AVC
req.alt-loc: avcstrm.h
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
ms.keywords: tagKS_DATARANGE_DV_AVC, KS_DATARANGE_DV_AVC, *PKS_DATARANGE_DV_AVC
req.iface: 
---

# tagKS_DATARANGE_DV_AVC structure



## -description
<p>The KS_DATARANGE_DV_AVC structure stores a range of AV/C digital video formats.</p>


## -syntax

````
typedef struct tagKS_DATARANGE_DV_AVC {
  KSDATARANGE       DataRange;
  DVINFO            DVVideoInfo;
  AVCPRECONNECTINFO ConnectInfo;
} KS_DATARANGE_DV_AVC, *PKS_DATARANGE_DV_AVC;
````


## -struct-fields
<dl>

### -field <b>DataRange</b>

<dd>
<p>Specifies the range of supported AV/C digital video formats.</p>
</dd>

### -field <b>DVVideoInfo</b>

<dd>
<p>Specifies the digital video information, for example, sound tracks and video information.</p>
</dd>

### -field <b>ConnectInfo</b>

<dd>
<p>Specifies the AV/C preconnection info.</p>
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
<dt>Avcstrm.h (include Avcstrm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561658">KSDATARANGE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559517">DVINFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554103">AVCPRECONNECTINFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KS_DATARANGE_DV_AVC structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
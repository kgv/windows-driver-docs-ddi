---
UID: NE.ntddcdrm._CDROM_PERFORMANCE_EXCEPTION_TYPE
title: CDROM_PERFORMANCE_EXCEPTION_TYPE
author: windows-driver-content
description: The CDROM_PERFORMANCE_EXCEPTION_TYPE enumeration defines the exceptional conditions for performance data.
old-location: storage\cdrom_performance_exception_type.htm
ms.assetid: 4AD156F8-911F-4D70-8B0E-8BB0D0747470
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddcdrm.h
req.include-header: Ntddcdrm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CDROM_PERFORMANCE_EXCEPTION_TYPE
req.alt-loc: Ntddcdrm.h
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
ms.keywords: OUTPUT_PACKET, OUTPUT_PACKET, *POUTPUT_PACKET
req.iface: 
---

# CDROM_PERFORMANCE_EXCEPTION_TYPE enumeration



## -description
<p>The <b>CDROM_PERFORMANCE_EXCEPTION_TYPE</b> enumeration defines the exceptional conditions for performance data. It is a member of the <a href="https://msdn.microsoft.com/library/windows/hardware/gg441233">CDROM_PERFORMANCE_REQUEST</a> structure, which is used as an input parameter to the  <a href="https://msdn.microsoft.com/library/windows/hardware/gg441242">IOCTL_CDROM_GET_PERFORMANCE</a> I/O control request. </p>


## -syntax

````
typedef enum _CDROM_PERFORMANCE_EXCEPTION_TYPE { 
  CdromNominalPerformance             = 1,
  CdromEntirePerformanceList          = 2,
     CdromPerformanceExceptionsOnly   = 3
} CDROM_PERFORMANCE_EXCEPTION_TYPE, *PCDROM_PERFORMANCE_EXCEPTION_TYPE;
````


## -enum-fields
<dl>

### -field <a id="CdromNominalPerformance"></a><a id="cdromnominalperformance"></a><a id="CDROMNOMINALPERFORMANCE"></a><b>CdromNominalPerformance</b>

<dd>
<p>Requests nominal performance parameters.</p>
</dd>

### -field <a id="CdromEntirePerformanceList"></a><a id="cdromentireperformancelist"></a><a id="CDROMENTIREPERFORMANCELIST"></a><b>CdromEntirePerformanceList</b>

<dd>
<p>Requests the entire performance list, as qualified by the <b>StartingLba</b> field of the <a href="https://msdn.microsoft.com/library/windows/hardware/gg441233">CDROM_PERFORMANCE_REQUEST</a> structure.</p>
</dd>

### -field <a id="___CdromPerformanceExceptionsOnly_"></a><a id="___cdromperformanceexceptionsonly_"></a><a id="___CDROMPERFORMANCEEXCEPTIONSONLY_"></a><b>   CdromPerformanceExceptionsOnly </b>

<dd>
<p>Requests only performance exceptions that cause the performance to fall outside the nominal.</p>
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
<dt>Ntddcdrm.h (include Ntddcdrm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/gg441233">CDROM_PERFORMANCE_REQUEST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/gg441242">IOCTL_CDROM_GET_PERFORMANCE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20CDROM_PERFORMANCE_EXCEPTION_TYPE enumeration%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
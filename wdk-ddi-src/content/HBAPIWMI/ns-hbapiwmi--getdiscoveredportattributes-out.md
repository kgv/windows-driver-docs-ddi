---
UID: NS.hbapiwmi._GetDiscoveredPortAttributes_OUT
title: GetDiscoveredPortAttributes_OUT
author: windows-driver-content
description: The GetDiscoveredPortAttributes_OUT structure is used to report the output parameter data of the GetDiscoveredPortAttributes WMI method to the WMI client.
old-location: storage\getdiscoveredportattributes_out.htm
ms.assetid: 7a6ae185-2f91-4285-b540-61130aef464c
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: hbapiwmi.h
req.include-header: Hbapiwmi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GetDiscoveredPortAttributes_OUT
req.alt-loc: hbapiwmi.h
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
ms.keywords: GetDiscoveredPortAttributes_OUT, GetDiscoveredPortAttributes_OUT, *PGetDiscoveredPortAttributes_OUT
req.iface: 
---

# GetDiscoveredPortAttributes_OUT structure



## -description
<p>The GetDiscoveredPortAttributes_OUT structure is used to report the output parameter data of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553925">GetDiscoveredPortAttributes</a> WMI method to the WMI client. </p>


## -syntax

````
typedef struct _GetDiscoveredPortAttributes_OUT {
  ULONG                         HBAStatus;
  MSFC_HBAPortAttributesResults PortAttributes;
} GetDiscoveredPortAttributes_OUT, *PGetDiscoveredPortAttributes_OUT;
````


## -struct-fields
<dl>

### -field <b>HBAStatus</b>

<dd>
<p>Contains a value associated with the WMI class qualifier <a href="https://msdn.microsoft.com/library/windows/hardware/ff557233">HBA_STATUS</a> that indicates the result of an HBA query operation.</p>
</dd>

### -field <b>PortAttributes</b>

<dd>
<p>Contains a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff562510">MSFC_HBAPortAttributesResults</a> that holds the port attributes to report.</p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite generates a declaration of the GetDiscoveredPortAttributes_IN structure in <i>Hbapiwmi.h </i>when it compiles the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562506">MSFC_HBAAdapterMethods WMI Class</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hbapiwmi.h (include Hbapiwmi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553925">GetDiscoveredPortAttributes</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20GetDiscoveredPortAttributes_OUT structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
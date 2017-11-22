---
UID: NS.iscsifnd._ISCSI_DiscoveredTargetPortalGroup2
title: ISCSI_DiscoveredTargetPortalGroup2
author: windows-driver-content
description: The ISCSI_DiscoveredTargetPortalGroup2 structure contains information about a discovered target portal group.
old-location: storage\iscsi_discoveredtargetportalgroup2.htm
ms.assetid: d852f062-3090-4a7a-bdb8-9dde93257a90
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsifnd.h
req.include-header: Iscsifnd.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ISCSI_DiscoveredTargetPortalGroup2
req.alt-loc: iscsifnd.h
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
ms.keywords: ISCSI_DiscoveredTargetPortalGroup2, ISCSI_DiscoveredTargetPortalGroup2, *PISCSI_DiscoveredTargetPortalGroup2
req.iface: 
---

# ISCSI_DiscoveredTargetPortalGroup2 structure



## -description
<p>The ISCSI_DiscoveredTargetPortalGroup2 structure contains information about a discovered target portal group.</p>


## -syntax

````
typedef struct _ISCSI_DiscoveredTargetPortalGroup2 {
  ULONG                         PortalCount;
  USHORT                        Tag;
  ISCSI_DiscoveredTargetPortal2 Portals[1];
} ISCSI_DiscoveredTargetPortalGroup2, *PISCSI_DiscoveredTargetPortalGroup2;
````


## -struct-fields
<dl>

### -field <b>PortalCount</b>

<dd>
<p>The number of portals in the group. </p>
</dd>

### -field <b>Tag</b>

<dd>
<p>A tag number that identifies the portal group. </p>
</dd>

### -field <b>Portals</b>

<dd>
<p>An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff561509">ISCSI_DiscoveredTargetPortal</a> structures, which describe target portals. </p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite automatically generates a declaration of the ISCSI_DiscoveredTargetPortalGroup2 structure when it compiles the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561520">ISCSI_DiscoveredTargetPortalGroup2 WMI Class</a> in <i>Discover.mof</i>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Iscsifnd.h (include Iscsifnd.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561509">ISCSI_DiscoveredTargetPortal</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561515">ISCSI_DiscoveredTargetPortalGroup</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561523">ISCSI_DiscoveredTargetPortalGroup WMI Class</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561520">ISCSI_DiscoveredTargetPortalGroup2 WMI Class</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ISCSI_DiscoveredTargetPortalGroup2 structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
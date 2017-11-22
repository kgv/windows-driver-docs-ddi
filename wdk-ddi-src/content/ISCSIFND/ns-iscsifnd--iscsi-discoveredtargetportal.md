---
UID: NS.iscsifnd._ISCSI_DiscoveredTargetPortal
title: ISCSI_DiscoveredTargetPortal
author: windows-driver-content
description: The ISCSI_DiscoveredTargetPortal structure provides information that is associated with a discovered target portal.
old-location: storage\iscsi_discoveredtargetportal.htm
ms.assetid: af5d0ad6-a035-4291-9390-889fdc3429ee
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
req.alt-api: ISCSI_DiscoveredTargetPortal
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
ms.keywords: ISCSI_DiscoveredTargetPortal, ISCSI_DiscoveredTargetPortal, *PISCSI_DiscoveredTargetPortal
req.iface: 
---

# ISCSI_DiscoveredTargetPortal structure



## -description
<p>The ISCSI_DiscoveredTargetPortal structure provides information that is associated with a discovered target portal. </p>


## -syntax

````
typedef struct _ISCSI_DiscoveredTargetPortal {
  USHORT           Socket;
  ISCSI_IP_Address Address;
  WCHAR            SymbolicName[256 + 1];
} ISCSI_DiscoveredTargetPortal, *PISCSI_DiscoveredTargetPortal;
````


## -struct-fields
<dl>

### -field <b>Socket</b>

<dd>
<p>The socket number of the portal. </p>
</dd>

### -field <b>Address</b>

<dd>
<p>The network address of the portal. </p>
</dd>

### -field <b>SymbolicName</b>

<dd>
<p>A wide character string that indicates the portal's symbolic name.</p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite automatically generates a declaration of the ISCSI_DiscoveredTargetPortal structure when it compiles the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561524">ISCSI_DiscoveredTargetPortal WMI Class</a> in <i>Discover.mof</i>. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561511">ISCSI_DiscoveredTargetPortal2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561524">ISCSI_DiscoveredTargetPortal WMI Class</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561574">ISCSI_TargetPortal</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ISCSI_DiscoveredTargetPortal structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
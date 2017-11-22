---
UID: NS.iscsimgt._ISCSI_PortalInfo
title: ISCSI_PortalInfo
author: windows-driver-content
description: The ISCSI_PortalInfo structure contains information about an iSCSI portal.
old-location: storage\iscsi_portalinfo.htm
ms.assetid: 0ecfed3e-477a-4014-8491-1a8997ac5b90
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsimgt.h
req.include-header: Iscsimgt.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ISCSI_PortalInfo
req.alt-loc: iscsimgt.h
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
ms.keywords: ISCSI_PortalInfo, ISCSI_PortalInfo, *PISCSI_PortalInfo
req.iface: 
---

# ISCSI_PortalInfo structure



## -description
<p>The ISCSI_PortalInfo structure contains information about an iSCSI portal. </p>


## -syntax

````
typedef struct _ISCSI_PortalInfo {
  ULONG            Index;
  UCHAR            PortalType;
  UCHAR            Protocol;
  UCHAR            Reserved1;
  UCHAR            Reserved2;
  ISCSI_IP_Address IPAddr;
  ULONG            Port;
  USHORT           PortalTag;
} ISCSI_PortalInfo, *PISCSI_PortalInfo;
````


## -struct-fields
<dl>

### -field <b>Index</b>

<dd>
<p>The unique port number associated with this portal.</p>
</dd>

### -field <b>PortalType</b>

<dd>
<p>The type of portal. This member can have the following symbolic constant values, which are defined in <i>Iscsimgt.h</i>.</p>
<table>
<tr>
<th>Portal Type</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>InitiatorPortals</p>
</td>
<td>
<p>The portal that the initiator uses to access the network. In an initiator, a portal is identified by its IP address. </p>
</td>
</tr>
<tr>
<td>
<p>TargetPortals</p>
</td>
<td>
<p>The portal that the target uses to access the network. In a target, a portal is identified by its IP address and its listening TCP port.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>Protocol</b>

<dd>
<p>The portal's transport protocol. Currently, this member must hold the value that is associated with the symbolic constant, TCP. TCP is defined in <i>Iscsimgt.h</i>.</p>
</dd>

### -field <b>Reserved1</b>

<dd>
<p>Reserved for Microsoft use only.</p>
</dd>

### -field <b>Reserved2</b>

<dd>
<p>Reserved for Microsoft use only.</p>
</dd>

### -field <b>IPAddr</b>

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff561536">ISCSI_IP_Address</a> structure that indicates the portal's network IP address.</p>
</dd>

### -field <b>Port</b>

<dd>
<p>The socket number for the portal.</p>
</dd>

### -field <b>PortalTag</b>

<dd>
<p>The portal group tag to which the portal belongs.</p>
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
<dt>Iscsimgt.h (include Iscsimgt.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561536">ISCSI_IP_Address</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561559">ISCSI_PortalInfo WMI Class</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ISCSI_PortalInfo structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
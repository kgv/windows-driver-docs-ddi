---
UID: NS.iscsicfg._MSiSCSI_DiscoveryConfig
title: MSiSCSI_DiscoveryConfig
author: windows-driver-content
description: The MSiSCSI_DiscoveryConfig structure contains information that indicates what methods an initiator uses to do discovery.
old-location: storage\msiscsi_discoveryconfig.htm
ms.assetid: fe2f4a93-3fdd-422b-afce-8def3ed6688e
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsicfg.h
req.include-header: Iscsicfg.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MSiSCSI_DiscoveryConfig
req.alt-loc: iscsicfg.h
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
ms.keywords: MSiSCSI_DiscoveryConfig, MSiSCSI_DiscoveryConfig, *PMSiSCSI_DiscoveryConfig
req.iface: 
---

# MSiSCSI_DiscoveryConfig structure



## -description
<p>The MSiSCSI_DiscoveryConfig structure contains information that indicates what methods an initiator uses to do discovery.</p>


## -syntax

````
typedef struct _MSiSCSI_DiscoveryConfig {
  BOOLEAN          PerformiSNSDiscovery;
  BOOLEAN          PerformSLPDiscovery;
  BOOLEAN          AutomaticiSNSDiscovery;
  WCHAR            InitiatorName[256 + 1];
  ISCSI_IP_Address iSNSServer;
} MSiSCSI_DiscoveryConfig, *PMSiSCSI_DiscoveryConfig;
````


## -struct-fields
<dl>

### -field <b>PerformiSNSDiscovery</b>

<dd>
<p>A Boolean value that indicates whether the initiator performs target discovery by using iSNS and a predetermined iSNS server. If this member is <b>TRUE</b>, the initiator performs target discovery by using iSNS and a predetermined iSNS server. If this member is <b>FALSE</b>, the initiator does not do discovery with iSNS.</p>
</dd>

### -field <b>PerformSLPDiscovery</b>

<dd>
<p>A Boolean value that indicates whether the initiator performs target discovery by using SLP. If this member is <b>TRUE</b>, the initiator performs target discovery by using SLP. </p>
</dd>

### -field <b>AutomaticiSNSDiscovery</b>

<dd>
<p>A Boolean value that indicates whether the initiator should automatically search for an iSNS server and then perform target discovery by using iSNS. If this member is <b>TRUE</b>, the initiator should automatically search for an iSNS server and then perform target discovery by using iSNS.</p>
</dd>

### -field <b>InitiatorName</b>

<dd>
<p>The default initiator name to register with the iSNS server. </p>
</dd>

### -field <b>iSNSServer</b>

<dd>
<p>If <b>AutomaticiSNSDiscovery</b> is <b>FALSE</b>, <b>iSNSServer</b> contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561536">ISCSI_IP_Address</a> structure that provides a fixed address of the iSNS server that is independent of the version of the IP protocol in use. </p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite automatically generates a declaration of the MSiSCSI_DiscoveryConfig structure when it compiles the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562995">MSiSCSI_DiscoveryConfig WMI Class</a> in <i>Config.mof</i>. </p>

<p>Initiators are required to implement the MSiSCSI_DiscoveryConfig class. You must implement this class.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Iscsicfg.h (include Iscsicfg.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562995">MSiSCSI_DiscoveryConfig WMI Class</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20MSiSCSI_DiscoveryConfig structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
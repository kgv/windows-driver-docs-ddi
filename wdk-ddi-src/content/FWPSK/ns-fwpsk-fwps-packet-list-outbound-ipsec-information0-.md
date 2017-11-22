---
UID: NS.fwpsk.FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0_
title: FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0_
author: windows-driver-content
description: The FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0 structure defines IPsec information associated with outbound packet data.Note  FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0 is a specific version of FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION.
old-location: netvista\fwps_packet_list_outbound_ipsec_information0.htm
ms.assetid: 18312157-f41c-474d-9cf4-446d8b189c4d
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0
req.alt-loc: fwpsk.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0_, FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0
req.iface: 
---

# FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0_ structure



## -description
<p>The <b>FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0</b> structure defines IPsec information associated with
  outbound packet data.</p>


## -syntax

````
typedef struct FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0_ {
  unsigned isIPsecPolicyMatch  :1;
  unsigned isTransportPolicyMatch  :1;
  unsigned isTunnelPolicyMatch  :1;
  unsigned isTunnelIPinIP  :1;
} FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0;
````


## -struct-fields
<dl>

### -field <b>isIPsecPolicyMatch</b>

<dd>
<p>A value that indicates whether the packet list matched an IPsec filter at the outbound transport
     layer.</p>
</dd>

### -field <b>isTransportPolicyMatch</b>

<dd>
<p>A value that indicates whether the packet list matched an IPsec transport mode filter at the outbound
     transport layer.</p>
</dd>

### -field <b>isTunnelPolicyMatch</b>

<dd>
<p>A value that indicates whether the packet list matched an IPsec tunnel mode filter at the outbound
     transport layer.</p>
</dd>

### -field <b>isTunnelIPinIP</b>

<dd>
<p>A value that indicates whether the packet list matched an IP-in-IP filter for IPsec tunnel mode.</p>
</dd>
</dl>

## -remarks
<p>An FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0 structure is included as a member of the 
    <a href="https://msdn.microsoft.com/bd005dd9-887a-4323-9816-e4a3b96ca53d">
    FWPS_PACKET_LIST_IPSEC_INFORMATION0</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fwpsk.h (include Fwpsk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/bd005dd9-887a-4323-9816-e4a3b96ca53d">
   FWPS_PACKET_LIST_IPSEC_INFORMATION0</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FWPS_PACKET_LIST_OUTBOUND_IPSEC_INFORMATION0 structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
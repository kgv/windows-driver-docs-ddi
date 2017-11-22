---
UID: NS.hbapiwmi._SendRPL_IN
title: SendRPL_IN
author: windows-driver-content
description: The SendRPL_IN structure is used to deliver input parameter data to the SendRPL WMI method.
old-location: storage\sendrpl_in.htm
ms.assetid: 0c084258-2bd6-47a8-a060-d4ba2734ebed
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
req.alt-api: SendRPL_IN
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
ms.keywords: SendRPL_IN, SendRPL_IN, *PSendRPL_IN
req.iface: 
---

# SendRPL_IN structure



## -description
<p>The SendRPL_IN structure is used to deliver input parameter data to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff565488">SendRPL</a> WMI method.</p>


## -syntax

````
typedef struct _SendRPL_IN {
  UCHAR PortWWN[8];
  UCHAR AgentWWN[8];
  ULONG agent_domain;
  ULONG portIndex;
} SendRPL_IN, *PSendRPL_IN;
````


## -struct-fields
<dl>

### -field <b>PortWWN</b>

<dd>
<p>Contains a worldwide name for the local port through which the read port list (RPL) command is sent. </p>
</dd>

### -field <b>AgentWWN</b>

<dd>
<p>Contains a worldwide name for the port that is to be queried for a list of ports of type FC_Port. For a definition of FC_Port, see the T11 committee's specification for <i>Fibre Channel HBA API</i>. </p>
</dd>

### -field <b>agent_domain</b>

<dd>
<p>Contains the domain number for the domain controller that is to be queried for a list of ports of type FC_Port. For a definition of FC_Port, see the T11 committee's specification for <i>Fibre Channel HBA API</i>. </p>
</dd>

### -field <b>portIndex</b>

<dd>
<p>Contains the port index of the first port in the list of ports of type FC_Port to be returned. </p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite generates a declaration of the SendRPL_IN structure in <i>Hbapiwmi.h </i>when it compiles the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562506">MSFC_HBAAdapterMethods WMI Class</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565488">SendRPL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20SendRPL_IN structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NE.ntddndis._NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION
title: NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION
author: windows-driver-content
description: The NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION enumeration specifies the interrupt moderation setting of a single root I/O virtualization (SR-IOV) virtual port (VPort) on the NIC switch.
old-location: netvista\ndis_nic_switch_vport_interrupt_moderation.htm
ms.assetid: 86ec2e8f-1a89-4c0a-b761-d9bf0d3dc35a
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.30 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION
req.alt-loc: Ntddndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: GET_CONFIGURATION_IOCTL_INPUT, GET_CONFIGURATION_IOCTL_INPUT, *PGET_CONFIGURATION_IOCTL_INPUT
req.iface: 
---

# NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION enumeration



## -description
<p>The <b>NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION</b> enumeration specifies the interrupt moderation setting of a single root I/O virtualization (SR-IOV) virtual port (VPort) on the NIC switch.</p>


## -syntax

````
typedef enum _NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION { 
  NdisNicSwitchVPortIntModUndefined  = 0,
  NdisNicSwitchVPortIntModAdaptive   = 1,
  NdisNicSwitchVPortIntModOff        = 2,
  NdisNicSwitchVPortIntModLow        = 100,
  NdisNicSwitchVPortIntModMedium     = 200,
  NdisNicSwitchVPortIntModHigh       = 300
} NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION, *PNDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION;
````


## -enum-fields
<dl>

### -field <a id="NdisNicSwitchVPortIntModUndefined"></a><a id="ndisnicswitchvportintmodundefined"></a><a id="NDISNICSWITCHVPORTINTMODUNDEFINED"></a><b>NdisNicSwitchVPortIntModUndefined</b>

<dd>
<p>Interrupt moderation for the VPort is not defined.</p>
</dd>

### -field <a id="NdisNicSwitchVPortIntModAdaptive"></a><a id="ndisnicswitchvportintmodadaptive"></a><a id="NDISNICSWITCHVPORTINTMODADAPTIVE"></a><b>NdisNicSwitchVPortIntModAdaptive</b>

<dd>
<p>Interrupt moderation for the VPort is adaptive. This state enables the network adapter to adjust the interrupt moderation rate for the VPort based on the pattern of network traffic.</p>
</dd>

### -field <a id="NdisNicSwitchVPortIntModOff"></a><a id="ndisnicswitchvportintmodoff"></a><a id="NDISNICSWITCHVPORTINTMODOFF"></a><b>NdisNicSwitchVPortIntModOff</b>

<dd>
<p>Interrupt moderation for the VPort is disabled.</p>
</dd>

### -field <a id="NdisNicSwitchVPortIntModLow"></a><a id="ndisnicswitchvportintmodlow"></a><a id="NDISNICSWITCHVPORTINTMODLOW"></a><b>NdisNicSwitchVPortIntModLow</b>

<dd>
<p>Interrupt moderation for the VPort is low.</p>
</dd>

### -field <a id="NdisNicSwitchVPortIntModMedium"></a><a id="ndisnicswitchvportintmodmedium"></a><a id="NDISNICSWITCHVPORTINTMODMEDIUM"></a><b>NdisNicSwitchVPortIntModMedium</b>

<dd>
<p>Interrupt moderation for the VPort is medium.</p>
</dd>

### -field <a id="NdisNicSwitchVPortIntModHigh"></a><a id="ndisnicswitchvportintmodhigh"></a><a id="NDISNICSWITCHVPORTINTMODHIGH"></a><b>NdisNicSwitchVPortIntModHigh</b>

<dd>
<p>Interrupt moderation for the VPort is high.</p>
</dd>
</dl>

## -remarks
<p>The determination of low, medium, and high interrupt moderation levels is determined by the miniport driver based on a hardware algorithm that is based on the network adapter.</p>

<p>The <b>InterruptModeration</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451597">NDIS_NIC_SWITCH_VPORT_PARAMETERS</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451594">NDIS_NIC_SWITCH_VPORT_INFO</a> structures is an NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION enumeration data type. </p>

<p>The determination of low, medium, and high interrupt moderation levels is determined by the miniport driver based on a hardware algorithm that is based on the network adapter.</p>

<p>The <b>InterruptModeration</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451597">NDIS_NIC_SWITCH_VPORT_PARAMETERS</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451594">NDIS_NIC_SWITCH_VPORT_INFO</a> structures is an NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION enumeration data type. </p>

<p>The determination of low, medium, and high interrupt moderation levels is determined by the miniport driver based on a hardware algorithm that is based on the network adapter.</p>

<p>The <b>InterruptModeration</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451597">NDIS_NIC_SWITCH_VPORT_PARAMETERS</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451594">NDIS_NIC_SWITCH_VPORT_INFO</a> structures is an NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION enumeration data type. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.30 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt><b></b></dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451594">NDIS_NIC_SWITCH_VPORT_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451597">NDIS_NIC_SWITCH_VPORT_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_NIC_SWITCH_VPORT_INTERRUPT_MODERATION enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
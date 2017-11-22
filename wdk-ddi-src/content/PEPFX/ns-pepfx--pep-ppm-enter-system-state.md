---
UID: NS.pepfx._PEP_PPM_ENTER_SYSTEM_STATE
title: PEP_PPM_ENTER_SYSTEM_STATE
author: windows-driver-content
description: Used in the PEP_NOTIFY_PPM_ENTER_SYSTEM_STATE notification to notify PEP that the system is about to enter a system power state.  .
old-location: kernel\pep_ppm_enter_system_state.htm
ms.assetid: 1a398899-b05d-4853-b68d-ae8be958dd91
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: pepfx.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1709
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PEP_PPM_ENTER_SYSTEM_STATE
req.alt-loc: Pepfx.h
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
ms.keywords: PEP_PPM_ENTER_SYSTEM_STATE, PEP_PPM_ENTER_SYSTEM_STATE, *PPEP_PPM_ENTER_SYSTEM_STATE
req.iface: 
---

# PEP_PPM_ENTER_SYSTEM_STATE structure



## -description
<p>Used in the <b>PEP_NOTIFY_PPM_ENTER_SYSTEM_STATE</b> notification to notify PEP that the system is about to enter a system power state.  </p>


## -syntax

````
typedef struct _PEP_PPM_ENTER_SYSTEM_STATE {
  SYSTEM_POWER_STATE  TargetState;
} PEP_PPM_ENTER_SYSTEM_STATE, *PPEP_PPM_ENTER_SYSTEM_STATE;
````


## -struct-fields
<dl>

### -field <b>TargetState</b>

<dd>
<p>On input, a <a href="https://msdn.microsoft.com/library/windows/hardware/ff564565">SYSTEM_POWER_STATE</a>-type value that indicates the power state that the system is entering. </p>
</dd>
</dl>

## -remarks
<p>This notification is sent to all processors simultaneously after the system has completed all passive level work transitioning the processor to the system power state. 
This notification is sent at DISPATCH_LEVEL, with all processors at dispatch. This notification is always executed on the target processor. 
PEP must not queue any work from this notification. The processors will not process work items, DPCs, etc. after this notification has been sent.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10, version 1709</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Pepfx.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt186881">Processor power management (PPM) notifications</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PEP_PPM_ENTER_SYSTEM_STATE structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
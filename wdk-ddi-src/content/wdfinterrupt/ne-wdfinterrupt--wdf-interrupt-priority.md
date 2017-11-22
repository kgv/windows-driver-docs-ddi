---
UID: NE.wdfinterrupt._WDF_INTERRUPT_PRIORITY
title: WDF_INTERRUPT_PRIORITY
author: windows-driver-content
description: The WDF_INTERRUPT_PRIORITY enumeration type identifies relative priorities for device interrupts.
old-location: wdf\wdf_interrupt_priority.htm
ms.assetid: e3305a9c-8107-4631-974b-fe85779ec8dc
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfinterrupt.h
req.include-header: Wdf.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WDF_INTERRUPT_PRIORITY
req.alt-loc: wdfinterrupt.h
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
ms.keywords: WDF_COINSTALLER_INSTALL_OPTIONS, WDF_COINSTALLER_INSTALL_OPTIONS, *PWDF_COINSTALLER_INSTALL_OPTIONS
req.iface: 
req.product: Windows 10 or later.
---

# WDF_INTERRUPT_PRIORITY enumeration



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WDF_INTERRUPT_PRIORITY</b> enumeration type identifies relative priorities for device interrupts.</p>


## -syntax

````
typedef enum _WDF_INTERRUPT_PRIORITY { 
  WdfIrqPriorityUndefined  = 0,
  WdfIrqPriorityLow        = 1,
  WdfIrqPriorityNormal     = 2,
  WdfIrqPriorityHigh       = 3
} WDF_INTERRUPT_PRIORITY, *PWDF_INTERRUPT_PRIORITY;
````


## -enum-fields
<dl>

### -field <a id="WdfIrqPriorityUndefined"></a><a id="wdfirqpriorityundefined"></a><a id="WDFIRQPRIORITYUNDEFINED"></a><b>WdfIrqPriorityUndefined</b>

<dd>
<p>The relative priority of a device's interrupt is undefined.</p>
</dd>

### -field <a id="WdfIrqPriorityLow"></a><a id="wdfirqprioritylow"></a><a id="WDFIRQPRIORITYLOW"></a><b>WdfIrqPriorityLow</b>

<dd>
<p>The device's interrupt has a relatively low priority, typically because the interrupt does not have to be serviced immediately.</p>
</dd>

### -field <a id="WdfIrqPriorityNormal"></a><a id="wdfirqprioritynormal"></a><a id="WDFIRQPRIORITYNORMAL"></a><b>WdfIrqPriorityNormal</b>

<dd>
<p>The device's interrupt priority is neither relatively low nor relatively high.</p>
</dd>

### -field <a id="WdfIrqPriorityHigh"></a><a id="wdfirqpriorityhigh"></a><a id="WDFIRQPRIORITYHIGH"></a><b>WdfIrqPriorityHigh</b>

<dd>
<p>The device's interrupt has a relatively high priority, typically because the interrupt must be serviced immediately.</p>
</dd>
</dl>

## -remarks
<p>The <b>WDF_INTERRUPT_PRIORITY</b> enumeration type is used as input to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff547387">WdfInterruptSetPolicy</a> method.</p>

<p>The <b>WDF_INTERRUPT_PRIORITY</b> enumeration type is used as input to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff547387">WdfInterruptSetPolicy</a> method.</p>

<p>The <b>WDF_INTERRUPT_PRIORITY</b> enumeration type is used as input to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff547387">WdfInterruptSetPolicy</a> method.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfinterrupt.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547387">WdfInterruptSetPolicy</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_INTERRUPT_PRIORITY enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
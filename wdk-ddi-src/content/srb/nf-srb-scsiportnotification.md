---
UID: NF.srb.ScsiPortNotification
title: ScsiPortNotification
author: windows-driver-content
description: The ScsiPortNotification routine informs the operating system-specific port driver of certain events, such as when a miniport driver completes a request or is ready to start another SRB, as well as when the HBA indicates certain SCSI error conditions that occurred during an operation.Note  The SCSI port driver and SCSI miniport driver models may be altered or unavailable in the future. Instead, we recommend using the Storport driver and Storport miniport driver models.
old-location: storage\scsiportnotification.htm
ms.assetid: 27da3881-4c47-492c-868e-ce72210e9d6f
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: srb.h
req.include-header: Miniport.h, Scsi.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ScsiPortNotification
req.alt-loc: scsiport.lib,scsiport.dll,storport.lib,storport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Scsiport.lib; 
Storport.lib
req.dll: 
req.irql: (See Remarks section)
ms.keywords: ScsiPortNotification
req.iface: 
req.product: Windows 10 or later.
---

# ScsiPortNotification function



## -description
<p>The <b>ScsiPortNotification</b> routine informs the operating system-specific port driver of certain events, such as when a miniport driver completes a request or is ready to start another SRB, as well as when the HBA indicates certain SCSI error conditions that occurred during an operation.</p>


## -syntax

````
VOID ScsiPortNotification(
   IN SCSI_NOTIFICATION_TYPE NotificationType,
   IN PVOID                  HwDeviceExtension
);
````


## -parameters
<dl>

### -param <i>NotificationType</i> 

<dd>
<p>Specifies the type of notification, which can be one of the following.</p>
<table>
<tr>
<th>Notification Type</th>
<th>Description</th>
</tr>
<tr>
<td>
<p><b>RequestComplete</b></p>
</td>
<td>
<p>Indicates the given <i>Srb</i> has finished. If this value is set, <b>ScsiPortNotification</b> requires one additional parameter: the address of the SRB. After this notification, the operating system-specific port driver owns the request. The miniport driver must not access the <i>Srb</i>, and it must not pass the <i>Srb</i> to another routine (such as <b>ScsiPortLogError</b>).</p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>RequestComplete</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564680">ScsiPortNotification (NotificationType = RequestComplete)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>NextRequest</b></p>
</td>
<td>
<p>Indicates the miniport driver is ready for another request to a target that is not currently busy. This notification should be sent by the miniport driver as soon as the driver is ready for another request. Usually, this notification is sent from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557323">HwScsiStartIo</a> routine but, sometimes, from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557312">HwScsiInterrupt</a> (or <a href="https://msdn.microsoft.com/library/windows/hardware/ff557295">HwScsiEnableInterruptsCallback</a>) routine.</p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>NextRequest</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564673">ScsiPortNotification (NotificationType = NextLuRequest)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>NextLuRequest</b></p>
</td>
<td>
<p>Indicates that the HBA is ready for another request for the specified logical unit. If this value is set, <b>ScsiPortNotification</b> requires three additional parameters: (1) the path ID, (2) the target ID, and (3) the logical unit number. This value should be used only if the HBA can queue multiple requests and support auto-request sense or tagged queuing. </p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>NextLuRequest</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564673">ScsiPortNotification (NotificationType = NextLuRequest)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>ResetDetected</b></p>
</td>
<td>
<p>Indicates that the HBA has detected a reset on the SCSI bus. After this notification, the miniport driver is still responsible for completing any active requests. The SCSI port driver will manage all required bus-reset delays.</p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>ResetDetected</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564689">ScsiPortNotification (NotificationType = ResetDetected)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>CallEnableInterrupts</b></p>
</td>
<td>
<p>Indicates that the miniport driver requires the operating system-specific port driver to call the miniport driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557295">HwScsiEnableInterruptsCallback</a> routine. If this value is set, <b>ScsiPortNotification</b> requires an additional parameter: the entry point for the <i>HwScsiEnableInterruptsCallback</i>. The miniport driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557312">HwScsiInterrupt</a> routine makes this call,<i> after </i>disabling interrupts on the HBA, to defer some interrupt-driven I/O processing if the HBA requires polling or stalling in the ISR. While the callback runs, system interrupts remain enabled but the miniport driver's <i>HwScsiInterrupt</i> routine will not be called. The <i>HwScsiEnableInterruptsCallback</i> is responsible for completing the deferred I/O processing and for calling <b>ScsiPortNotification</b> again with <b>CallDisableInterrupts</b> and the miniport driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557288">HwScsiDisableInterruptsCallback</a> entry point.</p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>CallEnableInterrupts</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564667">ScsiPortNotification (NotificationType = CallEnableInterrupts or CallDisableInterrupts)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>CallDisableInterrupts</b></p>
</td>
<td>
<p>Indicates that the miniport driver requires the operating system-specific port driver to call the miniport driver's <i>HwScsiDisableInterruptsCallback</i> routine. If this value is set, <b>ScsiPortNotification</b> requires an additional parameter: the entry point for the <i>HwScsiDisableInterruptsCallback</i>. While this callback runs, it cannot be preempted by an interrupt except from a device with a higher priority interrupt than the HBA. In this callback, the miniport driver reenables interrupts on the HBA.</p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>CallDisableInterrupts</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564667">ScsiPortNotification (NotificationType = CallEnableInterrupts or CallDisableInterrupts)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>RequestTimerCall</b></p>
</td>
<td>
<p>Indicates that the miniport driver requires the operating system-specific port driver to call the miniport driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557327">HwScsiTimer</a> routine in the requested number of microseconds. If this value is set, <b>ScsiPortNotification</b> requires two additional parameters: (1) the entry point for the miniport driver's <i>HwScsiTimer</i> routine, and (2) a <i>MiniportTimerValue</i> interval, in microseconds. Note that the resolution of the system timer is approximately 10 milliseconds.</p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>RequestTimerCall</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564686">ScsiPortNotification (NotificationType = RequestTimerCall)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>BusChangeDetected</b></p>
</td>
<td>
<p>Indicates that a target device might have been added or removed from a dynamic bus. If this value is set, <b>ScsiPortNotification</b> requires an additional parameter: the path ID of the bus on which the change was detected. After this notification, the port driver reenumerates the bus by issuing INQUIRY commands. Bus enumeration is time-consuming and ties up the bus, so a miniport driver should not send this notification unnecessarily </p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>BusChangeDetected</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564662">ScsiPortNotification (NotificationType = BusChangeDetected)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>WMIEvent</b></p>
</td>
<td>
<p>Indicates that the miniport driver has detected an event for which one or more WMI data consumers is registered. If this value is set, <b>ScsiPortNotification</b> requires at least three additional arguments: (1) a pointer to a WMI event structure, (2) the size of the event structure, and (3) the path ID of the target device if the event originated from a device, or 0Xff if the event originated from the adapter. If (3) is a path ID, <b>ScsiPortNotification</b> requires two additional arguments: (4) the target ID, and (5) the logical unit number (LUN) of the target device. </p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>WMIEvent</b>, see    </p>
<p>
<a href="https://msdn.microsoft.com/3b3857e6-43be-4e18-b7d3-c6f763ecb9e7">ScsiPortNotification (NotificationType = WMIEvent, PathId != 0xFF)</a>
</p>
</td>
</tr>
<tr>
<td>
<p><b>WMIReregister</b></p>
</td>
<td>
<p>Indicates that the miniport driver has changed the data items or the number of instances of a given data block previously registered by calling <b>IoWMIRegistrationControl</b>. If <b>WMIReregister</b> is set, <b>ScsiPortNotification</b> requires at least two additional arguments: (1) the path ID of the target device to reregister that device, or 0xFF to reregister the adapter. If (1) is a path ID, <b>ScsiPortNotification</b> requires two additional arguments: (2) the target ID, and (3) the logical unit number (LUN) of the target device. </p>
<p>For a description of the optional parameters used with a <i>NotificationType</i> of <b>WMIReregister</b>, see <a href="https://msdn.microsoft.com/8bb398fa-9aaa-46ee-8412-ac5f3046e2c2">ScsiPortNotification (NotificationType = WMIReregister, PathId != 0xFF)</a>
</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -param <i>HwDeviceExtension</i> 

<dd>
<p>Pointer to the hardware device extension. This is a per-HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the HBA's mapped access ranges. This area is available to the miniport driver in the <b>DeviceExtension-&gt;HwDeviceExtension</b> member of the HBA's device object immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff564645">ScsiPortInitialize</a>. The port driver frees this memory when it removes the device. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The <b>ScsiPortNotification</b> routine has a different set of optional parameters associated with each <i>NotificationType</i>. For a description of the optional parameters associated a particular <i>NotificationType</i>, see the reference page associated with that <i>NotificationType</i>. The following reference pages provide this information:</p><dl>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564680">ScsiPortNotification (NotificationType = RequestComplete)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564675">ScsiPortNotification (NotificationType = NextRequest)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564673">ScsiPortNotification (NotificationType = NextLuRequest)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564689">ScsiPortNotification (NotificationType = ResetDetected)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564667">ScsiPortNotification (NotificationType = CallEnableInterrupts or CallDisableInterrupts)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564686">ScsiPortNotification (NotificationType = RequestTimerCall)</a><b>)</b></p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564662">ScsiPortNotification (NotificationType = BusChangeDetected)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/3b3857e6-43be-4e18-b7d3-c6f763ecb9e7">ScsiPortNotification (NotificationType = WMIEvent, PathId != 0xFF)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/061e9066-d71e-4b92-bbd0-7906bc024c33">ScsiPortNotification (NotificationType = WMIEvent, PathId = 0xFF)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/8bb398fa-9aaa-46ee-8412-ac5f3046e2c2">ScsiPortNotification (NotificationType = WMIReregister, PathId != 0xFF)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/c094a810-742c-4b9a-9730-42a99e1acb75">ScsiPortNotification (NotificationType = WMIReregister, PathId = 0xFF)</a>
</p>
</dd>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564680">ScsiPortNotification (NotificationType = RequestComplete)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564675">ScsiPortNotification (NotificationType = NextRequest)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564673">ScsiPortNotification (NotificationType = NextLuRequest)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564689">ScsiPortNotification (NotificationType = ResetDetected)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564667">ScsiPortNotification (NotificationType = CallEnableInterrupts or CallDisableInterrupts)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564686">ScsiPortNotification (NotificationType = RequestTimerCall)</a><b>)</b></p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564662">ScsiPortNotification (NotificationType = BusChangeDetected)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/3b3857e6-43be-4e18-b7d3-c6f763ecb9e7">ScsiPortNotification (NotificationType = WMIEvent, PathId != 0xFF)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/061e9066-d71e-4b92-bbd0-7906bc024c33">ScsiPortNotification (NotificationType = WMIEvent, PathId = 0xFF)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/8bb398fa-9aaa-46ee-8412-ac5f3046e2c2">ScsiPortNotification (NotificationType = WMIReregister, PathId != 0xFF)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/c094a810-742c-4b9a-9730-42a99e1acb75">ScsiPortNotification (NotificationType = WMIReregister, PathId = 0xFF)</a>
</p>

<p>Every miniport driver must call <b>ScsiPortNotification</b> twice for each call to the miniport driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557323">HwScsiStartIo</a> routine with an SRB that the miniport driver completes successfully. First, the miniport driver calls <b>ScsiPortNotification</b> with the <i>NotificationType</i><b>NextRequest</b> or with <b>NextLuRequest</b> if the miniport driver supports tagged queuing or multiple requests per LU. Then, the miniport driver calls <b>ScsiPortNotification</b> with the <i>NotificationType</i><b>RequestComplete</b> and the request that it has just satisfied.</p>

<p>A miniport driver's <i>HwScsiInterrupt</i> routine is most likely to call <b>ScsiPortNotification</b> with the <i>NotificationType</i><b>ResetDetected</b>.</p>

<p>If an HBA requires the miniport driver to use more than a millisecond processing interrupt-driven I/O operations, its <i>HwScsiInterrupt</i> routine should disable interrupts on the HBA and call <b>ScsiPortNotification</b> with <b>CallEnableInterrupts</b> and a driver-supplied <i>HwScsiEnableInterruptsCallback</i> routine. This routine, in turn, calls <b>ScsiPortNotification</b> with <b>CallDisableInterrupts</b> and the corresponding driver-supplied <i>HwScsiDisableInterruptsCallback</i>.</p>

<p>A miniport driver that is registered as a WMI data provider can call <b>ScsiPortNotification</b> with <b>WMIEvent</b> to post an event for which it has previously received an enable request. The port driver queues the event in the interrupt data area of the miniport driver's device extension for later processing at a lower IRQL. Because only a limited number of events can be queued at one time, the miniport driver should use <b>WMIEvent</b> to signal exceptional rather than routine conditions, and it should give the port driver time to get back to DISPATCH_LEVEL between postings, to prevent events from being lost. </p>

<p>The <b>ScsiPortNotification</b> routine has a different set of optional parameters associated with each <i>NotificationType</i>. For a description of the optional parameters associated a particular <i>NotificationType</i>, see the reference page associated with that <i>NotificationType</i>. The following reference pages provide this information:</p><dl>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564680">ScsiPortNotification (NotificationType = RequestComplete)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564675">ScsiPortNotification (NotificationType = NextRequest)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564673">ScsiPortNotification (NotificationType = NextLuRequest)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564689">ScsiPortNotification (NotificationType = ResetDetected)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564667">ScsiPortNotification (NotificationType = CallEnableInterrupts or CallDisableInterrupts)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564686">ScsiPortNotification (NotificationType = RequestTimerCall)</a><b>)</b></p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564662">ScsiPortNotification (NotificationType = BusChangeDetected)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/3b3857e6-43be-4e18-b7d3-c6f763ecb9e7">ScsiPortNotification (NotificationType = WMIEvent, PathId != 0xFF)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/061e9066-d71e-4b92-bbd0-7906bc024c33">ScsiPortNotification (NotificationType = WMIEvent, PathId = 0xFF)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/8bb398fa-9aaa-46ee-8412-ac5f3046e2c2">ScsiPortNotification (NotificationType = WMIReregister, PathId != 0xFF)</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/c094a810-742c-4b9a-9730-42a99e1acb75">ScsiPortNotification (NotificationType = WMIReregister, PathId = 0xFF)</a>
</p>
</dd>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564680">ScsiPortNotification (NotificationType = RequestComplete)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564675">ScsiPortNotification (NotificationType = NextRequest)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564673">ScsiPortNotification (NotificationType = NextLuRequest)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564689">ScsiPortNotification (NotificationType = ResetDetected)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564667">ScsiPortNotification (NotificationType = CallEnableInterrupts or CallDisableInterrupts)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564686">ScsiPortNotification (NotificationType = RequestTimerCall)</a><b>)</b></p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564662">ScsiPortNotification (NotificationType = BusChangeDetected)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/3b3857e6-43be-4e18-b7d3-c6f763ecb9e7">ScsiPortNotification (NotificationType = WMIEvent, PathId != 0xFF)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/061e9066-d71e-4b92-bbd0-7906bc024c33">ScsiPortNotification (NotificationType = WMIEvent, PathId = 0xFF)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/8bb398fa-9aaa-46ee-8412-ac5f3046e2c2">ScsiPortNotification (NotificationType = WMIReregister, PathId != 0xFF)</a>
</p>

<p>
<a href="https://msdn.microsoft.com/c094a810-742c-4b9a-9730-42a99e1acb75">ScsiPortNotification (NotificationType = WMIReregister, PathId = 0xFF)</a>
</p>

<p>Every miniport driver must call <b>ScsiPortNotification</b> twice for each call to the miniport driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557323">HwScsiStartIo</a> routine with an SRB that the miniport driver completes successfully. First, the miniport driver calls <b>ScsiPortNotification</b> with the <i>NotificationType</i><b>NextRequest</b> or with <b>NextLuRequest</b> if the miniport driver supports tagged queuing or multiple requests per LU. Then, the miniport driver calls <b>ScsiPortNotification</b> with the <i>NotificationType</i><b>RequestComplete</b> and the request that it has just satisfied.</p>

<p>A miniport driver's <i>HwScsiInterrupt</i> routine is most likely to call <b>ScsiPortNotification</b> with the <i>NotificationType</i><b>ResetDetected</b>.</p>

<p>If an HBA requires the miniport driver to use more than a millisecond processing interrupt-driven I/O operations, its <i>HwScsiInterrupt</i> routine should disable interrupts on the HBA and call <b>ScsiPortNotification</b> with <b>CallEnableInterrupts</b> and a driver-supplied <i>HwScsiEnableInterruptsCallback</i> routine. This routine, in turn, calls <b>ScsiPortNotification</b> with <b>CallDisableInterrupts</b> and the corresponding driver-supplied <i>HwScsiDisableInterruptsCallback</i>.</p>

<p>A miniport driver that is registered as a WMI data provider can call <b>ScsiPortNotification</b> with <b>WMIEvent</b> to post an event for which it has previously received an enable request. The port driver queues the event in the interrupt data area of the miniport driver's device extension for later processing at a lower IRQL. Because only a limited number of events can be queued at one time, the miniport driver should use <b>WMIEvent</b> to signal exceptional rather than routine conditions, and it should give the port driver time to get back to DISPATCH_LEVEL between postings, to prevent events from being lost. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Srb.h (include Miniport.h or Scsi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Scsiport.lib; </dt>
<dt>Storport.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>(See Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557327">HwScsiTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557288">HwScsiDisableInterruptsCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557295">HwScsiEnableInterruptsCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564608">ScsiPortCompleteRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550480">IoWMIRegistrationControl</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ScsiPortNotification routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
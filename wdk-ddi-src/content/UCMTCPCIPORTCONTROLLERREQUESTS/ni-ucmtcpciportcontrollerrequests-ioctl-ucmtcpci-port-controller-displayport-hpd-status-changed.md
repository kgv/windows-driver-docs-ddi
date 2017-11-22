---
UID: NI.ucmtcpciportcontrollerrequests.IOCTL_UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED
title: IOCTL_UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED
author: windows-driver-content
description: Notifies the client driver that the hot-plug detect status of the DisplayPort connection has changed so that the driver can perform additional tasks.
old-location: buses\ioctl_ucmtcpci_port_controller_displayport_hpd_status_changed.htm
ms.assetid: 5FF692BE-14D2-403A-B7B3-C13CAFBECE05
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: usbref
req.header: ucmtcpciportcontrollerrequests.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED
req.alt-loc: UcmTcpciPortControllerRequests.h
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
ms.keywords: UCMTCPCI_PORT_CONTROLLER_IDENTIFICATION, UCMTCPCI_PORT_CONTROLLER_IDENTIFICATION, *PUCMTCPCI_PORT_CONTROLLER_IDENTIFICATION
req.iface: 
req.product: Windows 10 or later.
---

# IOCTL_UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED IOCTL



## -description
<p>Notifies the client driver that the hot-plug detect status of the DisplayPort connection has changed so that the driver can perform additional tasks.</p>


## -ioctlparameters

### -input-buffer
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt805874">UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED_IN_PARAMS</a> structure that contains status information.</p>

<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt805874">UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED_IN_PARAMS</a> structure that contains status information.</p>

### -input-buffer-length
<p>The size of <a href="https://msdn.microsoft.com/library/windows/hardware/mt805874">UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED_IN_PARAMS</a>.</p>

<p>The size of <a href="https://msdn.microsoft.com/library/windows/hardware/mt805874">UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED_IN_PARAMS</a>.</p>

<p>The size of <a href="https://msdn.microsoft.com/library/windows/hardware/mt805874">UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED_IN_PARAMS</a>.</p>

### -output-buffer

<text></text>

### -output-buffer-length

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

## -remarks
<p>The UcmTcpciCx class extension sends this IOCTL request when the DisplayPort mode status changes. The client driver can determine the new status based on the values passed in the supplied structure.</p>

<p>The UcmTcpciCx class extension sends this IOCTL request when the DisplayPort mode status changes. The client driver can determine the new status based on the values passed in the supplied structure.</p>

<p>The UcmTcpciCx class extension sends this IOCTL request when the DisplayPort mode status changes. The client driver can determine the new status based on the values passed in the supplied structure.</p>

<p>The UcmTcpciCx class extension sends this IOCTL request when the DisplayPort mode status changes. The client driver can determine the new status based on the values passed in the supplied structure.</p>

<p>The UcmTcpciCx class extension sends this IOCTL request when the DisplayPort mode status changes. The client driver can determine the new status based on the values passed in the supplied structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
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
<dt>UcmTcpciPortControllerRequests.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542894">Creating IOCTL Requests in Drivers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548651">WdfIoTargetSendInternalIoctlOthersSynchronously</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548656">WdfIoTargetSendInternalIoctlSynchronously</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548660">WdfIoTargetSendIoctlSynchronously</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20IOCTL_UCMTCPCI_PORT_CONTROLLER_DISPLAYPORT_HPD_STATUS_CHANGED control code%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
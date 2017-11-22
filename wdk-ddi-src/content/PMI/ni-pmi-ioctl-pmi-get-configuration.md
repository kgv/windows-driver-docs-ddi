---
UID: NI.pmi.IOCTL_PMI_GET_CONFIGURATION
title: IOCTL_PMI_GET_CONFIGURATION
author: windows-driver-content
description: The IOCTL_PMI_GET_CONFIGURATION request returns information about the current configuration of a power meter.
old-location: powermeter\ioctl_pmi_get_configuration.htm
ms.assetid: 957a2658-dddc-4529-8697-5fa44fcb96c2
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: powermeter
req.header: pmi.h
req.include-header: Pmi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7, Windows Server 2008 R2, and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_PMI_GET_CONFIGURATION
req.alt-loc: Pmi.h
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
ms.keywords: PO_FX_CORE_DEVICE, PO_FX_CORE_DEVICE, *PPO_FX_CORE_DEVICE
req.iface: 
---

# IOCTL_PMI_GET_CONFIGURATION IOCTL



## -description
<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request returns information about the current configuration of a power meter.</p>


## -ioctlparameters

### -input-buffer
<p>The <b>AssociatedIrp.SystemBuffer</b> member of the I/O request packet (IRP) points to an initiator-allocated buffer that is used both as the input buffer and the output buffer for the request. On input, this buffer contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure in which the <b>Version</b> and <b>ConfigurationType</b> members are set to valid values. The <b>ConfigurationType</b> member contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value that specifies the type of configuration information to be retrieved from the power meter. This value also determines the type of configuration information to be written to the output buffer.</p>

### -input-buffer-length
<p>The <b>Parameters.DeviceIoControl.InputBufferLength</b> member of the IRP's current I/O stack location (<a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a>) is set to the size in bytes of the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member. This size must be greater than or equal to <b>sizeof</b>(<b>PMI_CONFIGURATION</b>) or the request will fail with an error status of STATUS_INVALID_PARAMETER.</p>

<p>The <b>Parameters.DeviceIoControl.InputBufferLength</b> member of the IRP's current I/O stack location (<a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a>) is set to the size in bytes of the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member. This size must be greater than or equal to <b>sizeof</b>(<b>PMI_CONFIGURATION</b>) or the request will fail with an error status of STATUS_INVALID_PARAMETER.</p>

### -output-buffer
<p>If the request completes successfully, the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure. This structure contains the requested configuration information.</p>

<p>If the request completes successfully, the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure. This structure contains the requested configuration information.</p>

<p>If the request completes successfully, the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure. This structure contains the requested configuration information.</p>

### -output-buffer-length
<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the IRP's current I/O stack location is set to the size in bytes of the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member. For the request to succeed, this size must be greater than or equal to <b>sizeof</b>(<b>PMI_CONFIGURATION</b>). Otherwise, the request will fail with an error status of STATUS_BUFFER_TOO_SMALL.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the IRP's current I/O stack location is set to the size in bytes of the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member. For the request to succeed, this size must be greater than or equal to <b>sizeof</b>(<b>PMI_CONFIGURATION</b>). Otherwise, the request will fail with an error status of STATUS_BUFFER_TOO_SMALL.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the IRP's current I/O stack location is set to the size in bytes of the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member. For the request to succeed, this size must be greater than or equal to <b>sizeof</b>(<b>PMI_CONFIGURATION</b>). Otherwise, the request will fail with an error status of STATUS_BUFFER_TOO_SMALL.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the IRP's current I/O stack location is set to the size in bytes of the buffer pointed to by the <b>AssociatedIrp.SystemBuffer</b> member. For the request to succeed, this size must be greater than or equal to <b>sizeof</b>(<b>PMI_CONFIGURATION</b>). Otherwise, the request will fail with an error status of STATUS_BUFFER_TOO_SMALL.</p>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p>The <b>Information</b> member is set to the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The WDM driver that supports the PMI interface has completed the IOCTL request successfully.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a> is less than the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The initiator-allocated input buffer contains an invalid <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> value.</p>

<p>The <b>Information</b> member is set to the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The WDM driver that supports the PMI interface has completed the IOCTL request successfully.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a> is less than the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The initiator-allocated input buffer contains an invalid <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> value.</p>

<p>The <b>Information</b> member is set to the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The WDM driver that supports the PMI interface has completed the IOCTL request successfully.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a> is less than the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The initiator-allocated input buffer contains an invalid <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> value.</p>

<p>The <b>Information</b> member is set to the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The WDM driver that supports the PMI interface has completed the IOCTL request successfully.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a> is less than the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The initiator-allocated input buffer contains an invalid <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> value.</p>

<p>The <b>Information</b> member is set to the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The WDM driver that supports the PMI interface has completed the IOCTL request successfully.</p>

<p>The <b>Parameters.DeviceIoControl.OutputBufferLength</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a> is less than the size, in bytes, of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure.</p>

<p>The initiator-allocated input buffer contains an invalid <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> value.</p>

## -remarks
<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request queries the current configuration of the power meter. The input <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value specifies the type of configuration data to be returned. The data type and contents of the output buffer vary based on the data requested.</p>

<p>The following table describes the type of data that is returned for the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value.</p>

<p><b>PmiBudgetingConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a> structure that contains information about the budgeting configuration of the power meter.</p>

<p><b>PmiMeasurementConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a> structure that contains information about the measurement configuration of the power meter.</p>

<p><b>PmiThresholdConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a> structure that contains information about the threshold configuration of the power meter.</p>

<p> </p>

<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request queries the current configuration of the power meter. The input <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value specifies the type of configuration data to be returned. The data type and contents of the output buffer vary based on the data requested.</p>

<p>The following table describes the type of data that is returned for the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value.</p>

<p><b>PmiBudgetingConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a> structure that contains information about the budgeting configuration of the power meter.</p>

<p><b>PmiMeasurementConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a> structure that contains information about the measurement configuration of the power meter.</p>

<p><b>PmiThresholdConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a> structure that contains information about the threshold configuration of the power meter.</p>

<p> </p>

<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request queries the current configuration of the power meter. The input <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value specifies the type of configuration data to be returned. The data type and contents of the output buffer vary based on the data requested.</p>

<p>The following table describes the type of data that is returned for the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value.</p>

<p><b>PmiBudgetingConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a> structure that contains information about the budgeting configuration of the power meter.</p>

<p><b>PmiMeasurementConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a> structure that contains information about the measurement configuration of the power meter.</p>

<p><b>PmiThresholdConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a> structure that contains information about the threshold configuration of the power meter.</p>

<p> </p>

<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request queries the current configuration of the power meter. The input <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value specifies the type of configuration data to be returned. The data type and contents of the output buffer vary based on the data requested.</p>

<p>The following table describes the type of data that is returned for the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value.</p>

<p><b>PmiBudgetingConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a> structure that contains information about the budgeting configuration of the power meter.</p>

<p><b>PmiMeasurementConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a> structure that contains information about the measurement configuration of the power meter.</p>

<p><b>PmiThresholdConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a> structure that contains information about the threshold configuration of the power meter.</p>

<p> </p>

<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request queries the current configuration of the power meter. The input <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value specifies the type of configuration data to be returned. The data type and contents of the output buffer vary based on the data requested.</p>

<p>The following table describes the type of data that is returned for the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value.</p>

<p><b>PmiBudgetingConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a> structure that contains information about the budgeting configuration of the power meter.</p>

<p><b>PmiMeasurementConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a> structure that contains information about the measurement configuration of the power meter.</p>

<p><b>PmiThresholdConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a> structure that contains information about the threshold configuration of the power meter.</p>

<p> </p>

<p>The <b>IOCTL_PMI_GET_CONFIGURATION</b> request queries the current configuration of the power meter. The input <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value specifies the type of configuration data to be returned. The data type and contents of the output buffer vary based on the data requested.</p>

<p>The following table describes the type of data that is returned for the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumeration value.</p>

<p><b>PmiBudgetingConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a> structure that contains information about the budgeting configuration of the power meter.</p>

<p><b>PmiMeasurementConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a> structure that contains information about the measurement configuration of the power meter.</p>

<p><b>PmiThresholdConfiguration</b></p>

<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a> structure that contains information about the threshold configuration of the power meter.</p>

<p> </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7, Windows Server 2008 R2, and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Pmi.h (include Pmi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543837">IOCTL_PMI_GET_CAPABILITIES</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543858">PMI_BUDGETING_CONFIGURATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543864">PMI_CAPABILITIES_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543887">PMI_MEASUREMENT_CONFIGURATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543908">PMI_THRESHOLD_CONFIGURATION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [powermeter\powermeter]:%20IOCTL_PMI_GET_CONFIGURATION control code%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
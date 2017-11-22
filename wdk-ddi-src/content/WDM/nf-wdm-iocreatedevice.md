---
UID: NF.wdm.IoCreateDevice
title: IoCreateDevice
author: windows-driver-content
description: The IoCreateDevice routine creates a device object for use by a driver.
old-location: kernel\iocreatedevice.htm
ms.assetid: 54ca9dc8-8095-4b62-9ebc-f297abb429ca
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCreateDevice
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: AddDevice, CheckDeviceObjectFlags, IrqlIoPassive1, MiniportOnlyWdmDevice, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
ms.keywords: IoCreateDevice
req.iface: 
req.product: Windows 10 or later.
---

# IoCreateDevice function



## -description
<p>The <b>IoCreateDevice</b> routine creates a device object for use by a driver.</p>


## -syntax

````
NTSTATUS IoCreateDevice(
  _In_     PDRIVER_OBJECT  DriverObject,
  _In_     ULONG           DeviceExtensionSize,
  _In_opt_ PUNICODE_STRING DeviceName,
  _In_     DEVICE_TYPE     DeviceType,
  _In_     ULONG           DeviceCharacteristics,
  _In_     BOOLEAN         Exclusive,
  _Out_    PDEVICE_OBJECT  *DeviceObject
);
````


## -parameters
<dl>

### -param <i>DriverObject</i> [in]

<dd>
<p>Pointer to the driver object for the caller. Each driver receives a pointer to its driver object in a parameter to its <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine. WDM function and filter drivers also receive a driver object pointer in their <a href="https://msdn.microsoft.com/library/windows/hardware/ff540521">AddDevice</a> routines.</p>
</dd>

### -param <i>DeviceExtensionSize</i> [in]

<dd>
<p>Specifies the driver-determined number of bytes to be allocated for the <a href="https://msdn.microsoft.com/9ea59994-1112-4ae5-96a8-fa0670694b53">device extension</a> of the device object. The internal structure of the device extension is driver-defined.</p>
</dd>

### -param <i>DeviceName</i> [in, optional]

<dd>
<p>Optionally points to a buffer containing a null-terminated Unicode string that names the device object. The string must be a full path name. WDM filter and function drivers do not name their device objects. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff556420">Named Device Objects</a>.
     </p>
<div class="alert"><b>Note</b>  If a device name is not supplied (that is, <i>DeviceName</i> is <b>NULL</b>), the device object created by <b>IoCreateDevice</b> will not (and cannot) have a discretionary access control list (DACL) associated with it. For additional information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563698">Security Descriptors</a>.</div>
<div> </div>
</dd>

### -param <i>DeviceType</i> [in]

<dd>
<p>Specifies one of the system-defined FILE_DEVICE_<i>XXX</i> constants that indicate the type of device (such as FILE_DEVICE_DISK or FILE_DEVICE_KEYBOARD) or a vendor-defined value for a new type of device. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563821">Specifying Device Types</a>.</p>
</dd>

### -param <i>DeviceCharacteristics</i> [in]

<dd>
<p>Specifies one or more system-defined constants, ORed together, that provide additional information about the driver's device. For a list of possible device characteristics, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a>. For more information about how to specify device characteristics, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563818">Specifying Device Characteristics</a>. Most drivers specify FILE_DEVICE_SECURE_OPEN for this parameter.</p>
</dd>

### -param <i>Exclusive</i> [in]

<dd>
<p>Specifies if the device object represents an <a href="wdkgloss.e#wdkgloss.exclusive_device#wdkgloss.exclusive_device"><i>exclusive device</i></a>. Most drivers set this value to <b>FALSE</b>. For more information about exclusive access, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563827">Specifying Exclusive Access to Device Objects</a>.</p>
</dd>

### -param <i>DeviceObject</i> [out]

<dd>
<p>Pointer to a variable that receives a pointer to the newly created <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure. The <b>DEVICE_OBJECT</b> structure is allocated from nonpaged pool.</p>
</dd>
</dl>

## -returns
<p><b>IoCreateDevice</b> returns STATUS_SUCCESS on success, or the appropriate NTSTATUS error code on failure. A partial list of the failure codes returned by this function includes:</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
<dt><b>STATUS_OBJECT_NAME_COLLISION</b></dt>
</dl>

## -remarks
<p><b>IoCreateDevice</b> creates a device object and returns a pointer to the object. The caller is responsible for deleting the object when it is no longer needed by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549083">IoDeleteDevice</a>.</p>

<p><b>IoCreateDevice</b> can only be used to create an unnamed device object, or a named device object for which a security descriptor is set by an INF file. Otherwise, drivers must use <a href="https://msdn.microsoft.com/library/windows/hardware/ff548407">IoCreateDeviceSecure</a> to create named device objects. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff542862">Creating a Device Object</a>. The caller is responsible for setting certain members of the returned device object. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff547807">Initializing a Device Object</a> and the device-type-specific documentation for your device.</p>

<p>Be careful to specify the <i>DeviceType</i> and <i>DeviceCharacteristics</i> values in the correct parameters. Both parameters use system-defined FILE_<i>XXX</i> constants and some driver writers specify the values in the wrong parameters by mistake.</p>

<p>A remote file system that creates a named device object for a network redirector, and that registers using <a href="https://msdn.microsoft.com/library/windows/hardware/ff547178">FsRtlRegisterUncProvider</a>, must specify FILE_REMOTE_DEVICE as one of the options in the <i>DeviceCharacteristics</i> parameter of <b>IoCreateDevice</b>.</p>

<p>Device objects for disks, tapes, CD-ROMs, and RAM disks are given a Volume Parameter Block (VPB) that is initialized to indicate that the volume has never been mounted on the device.</p>

<p>If a driver's call to <b>IoCreateDevice</b> returns an error, the driver should release any resources that it allocated for that device.</p>

<p><b>IoCreateDevice</b> creates a device object and returns a pointer to the object. The caller is responsible for deleting the object when it is no longer needed by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549083">IoDeleteDevice</a>.</p>

<p><b>IoCreateDevice</b> can only be used to create an unnamed device object, or a named device object for which a security descriptor is set by an INF file. Otherwise, drivers must use <a href="https://msdn.microsoft.com/library/windows/hardware/ff548407">IoCreateDeviceSecure</a> to create named device objects. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff542862">Creating a Device Object</a>. The caller is responsible for setting certain members of the returned device object. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff547807">Initializing a Device Object</a> and the device-type-specific documentation for your device.</p>

<p>Be careful to specify the <i>DeviceType</i> and <i>DeviceCharacteristics</i> values in the correct parameters. Both parameters use system-defined FILE_<i>XXX</i> constants and some driver writers specify the values in the wrong parameters by mistake.</p>

<p>A remote file system that creates a named device object for a network redirector, and that registers using <a href="https://msdn.microsoft.com/library/windows/hardware/ff547178">FsRtlRegisterUncProvider</a>, must specify FILE_REMOTE_DEVICE as one of the options in the <i>DeviceCharacteristics</i> parameter of <b>IoCreateDevice</b>.</p>

<p>Device objects for disks, tapes, CD-ROMs, and RAM disks are given a Volume Parameter Block (VPB) that is initialized to indicate that the volume has never been mounted on the device.</p>

<p>If a driver's call to <b>IoCreateDevice</b> returns an error, the driver should release any resources that it allocated for that device.</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540521">AddDevice</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975142">CheckDeviceObjectFlags</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547763">IrqlIoPassive1</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975092">MiniportOnlyWdmDevice</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/f3522315-cf15-41f7-ac87-c625c7dc8040"> DEVICE_OBJECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547178">FsRtlRegisterUncProvider</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548294">IoAttachDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548300">IoAttachDeviceToDeviceStack</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548407">IoCreateDeviceSecure</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549043">IoCreateSymbolicLink</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549083">IoDeleteDevice</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoCreateDevice routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
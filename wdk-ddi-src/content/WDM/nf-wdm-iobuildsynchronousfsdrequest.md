---
UID: NF.wdm.IoBuildSynchronousFsdRequest
title: IoBuildSynchronousFsdRequest
author: windows-driver-content
description: The IoBuildSynchronousFsdRequest routine allocates and sets up an IRP for a synchronously processed I/O request.
old-location: kernel\iobuildsynchronousfsdrequest.htm
ms.assetid: b6d257cb-5384-44fe-bcff-67c67439ad08
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
req.alt-api: IoBuildSynchronousFsdRequest
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: ForwardedAtBadIrqlFsdSync, IoBuildSynchronousFsdRequestNoFree, IoBuildSynchronousFsdRequestWait, IoBuildSynchronousFsdRequestWaitTimeout, PowerIrpDDis, SignalEventInCompletion, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
ms.keywords: IoBuildSynchronousFsdRequest
req.iface: 
req.product: Windows 10 or later.
---

# IoBuildSynchronousFsdRequest function



## -description
<p>The <b>IoBuildSynchronousFsdRequest</b> routine allocates and sets up an IRP for a synchronously processed I/O request.</p>


## -syntax

````
PIRP IoBuildSynchronousFsdRequest(
  _In_     ULONG            MajorFunction,
  _In_     PDEVICE_OBJECT   DeviceObject,
  _Inout_  PVOID            Buffer,
  _In_opt_ ULONG            Length,
  _In_opt_ PLARGE_INTEGER   StartingOffset,
  _In_     PKEVENT          Event,
  _Out_    PIO_STATUS_BLOCK IoStatusBlock
);
````


## -parameters
<dl>

### -param <i>MajorFunction</i> [in]

<dd>
<p>The major function code for the IRP. This code can be <a href="https://msdn.microsoft.com/library/windows/hardware/ff549268">IRP_MJ_PNP</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff549327">IRP_MJ_READ</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550819">IRP_MJ_WRITE</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff549235">IRP_MJ_FLUSH_BUFFERS</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff549423">IRP_MJ_SHUTDOWN</a>.</p>
</dd>

### -param <i>DeviceObject</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure for the next-lower driver's device object, which represents the target device.</p>
</dd>

### -param <i>Buffer</i> [in, out]

<dd>
<p>A pointer to a data buffer. If <i>MajorFunction</i> is <b>IRP_MJ_WRITE</b>, the buffer contains data to be written. If <i>MajorFunction</i> is <b>IRP_MJ_READ</b>, the buffer receives data. If <i>MajorFunction</i> is <b>IRP_MJ_FLUSH_BUFFERS</b> or <b>IRP_MJ_SHUTDOWN</b>, this parameter must be <b>NULL</b>.</p>
</dd>

### -param <i>Length</i> [in, optional]

<dd>
<p>The length, in bytes, of the buffer pointed to by <i>Buffer</i>. For devices such as disks, this value must be an integer multiple of the sector size. Starting with Windows 8, the sector size can be 4,096 or 512 bytes. In earlier versions of Windows, the sector size is always 512 bytes. This parameter is required for read and write requests, but must be zero for flush and shutdown requests.</p>
</dd>

### -param <i>StartingOffset</i> [in, optional]

<dd>
<p>A pointer to the offset on the disk, for read and write requests. The units and meaning of this value are driver-specific. This parameter is required for read and write requests, but must be zero for flush and shutdown requests.</p>
</dd>

### -param <i>Event</i> [in]

<dd>
<p>A pointer to a caller-allocated and initialized event object. The I/O manager sets the event to the Signaled state when a lower-level driver completes the requested operation. After calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff548336">IoCallDriver</a>, the driver can wait for the event object.</p>
</dd>

### -param <i>IoStatusBlock</i> [out]

<dd>
<p>A pointer to a location that receives the I/O status block that is set when the IRP is completed by a lower-level driver.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, <b>IoBuildSynchronousFsdRequest</b> returns a pointer to an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a> structure, with the next-lower driver's I/O stack location set up from the supplied parameters. Otherwise, the routine returns <b>NULL</b>.</p>

## -remarks
<p>A file system driver (FSD) or other higher-level driver can call <b>IoBuildSynchronousFsdRequest</b> to set up IRPs that it synchronously sends to lower-level drivers.</p>

<p><b>IoBuildSynchronousFsdRequest</b> allocates and sets up an IRP that requests lower-level drivers to perform a synchronous read, write, flush, or shutdown operation. The IRP contains enough information to start the operation.</p>

<p>Lower-level drivers might impose restrictions on parameters supplied to this routine. For example, disk drivers might require that values supplied for <i>Length</i> and <i>StartingOffset</i> be integer multiples of the device's sector size.</p>

<p>After calling <b>IoBuildSynchronousFsdRequest</b> to create a request, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548336">IoCallDriver</a> to send the request to the next-lower driver. If <b>IoCallDriver</b> returns STATUS_PENDING, the driver must wait for the completion of the IRP by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff553350">KeWaitForSingleObject</a> on the given <i>Event</i>. Most drivers do not need to set an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548354">IoCompletion</a> routine for the IRP. </p>

<p>IRPs that are created by <b>IoBuildSynchronousFsdRequest</b> must be completed by a driver's call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff548343">IoCompleteRequest</a>. A driver that calls <b>IoBuildSynchronousFsdRequest</b> must not call <a href="https://msdn.microsoft.com/library/windows/hardware/hh454223">IoFreeIrp</a>, because the I/O manager frees these synchronous IRPs after <b>IoCompleteRequest</b> has been called. </p>

<p><b>IoBuildSynchronousFsdRequest</b> queues the IRPs that it creates to an IRP queue that is specific to the current thread. If the thread exits, the I/O manager cancels the IRP. </p>

<p>A file system driver (FSD) or other higher-level driver can call <b>IoBuildSynchronousFsdRequest</b> to set up IRPs that it synchronously sends to lower-level drivers.</p>

<p><b>IoBuildSynchronousFsdRequest</b> allocates and sets up an IRP that requests lower-level drivers to perform a synchronous read, write, flush, or shutdown operation. The IRP contains enough information to start the operation.</p>

<p>Lower-level drivers might impose restrictions on parameters supplied to this routine. For example, disk drivers might require that values supplied for <i>Length</i> and <i>StartingOffset</i> be integer multiples of the device's sector size.</p>

<p>After calling <b>IoBuildSynchronousFsdRequest</b> to create a request, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548336">IoCallDriver</a> to send the request to the next-lower driver. If <b>IoCallDriver</b> returns STATUS_PENDING, the driver must wait for the completion of the IRP by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff553350">KeWaitForSingleObject</a> on the given <i>Event</i>. Most drivers do not need to set an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548354">IoCompletion</a> routine for the IRP. </p>

<p>IRPs that are created by <b>IoBuildSynchronousFsdRequest</b> must be completed by a driver's call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff548343">IoCompleteRequest</a>. A driver that calls <b>IoBuildSynchronousFsdRequest</b> must not call <a href="https://msdn.microsoft.com/library/windows/hardware/hh454223">IoFreeIrp</a>, because the I/O manager frees these synchronous IRPs after <b>IoCompleteRequest</b> has been called. </p>

<p><b>IoBuildSynchronousFsdRequest</b> queues the IRPs that it creates to an IRP queue that is specific to the current thread. If the thread exits, the I/O manager cancels the IRP. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975149">ForwardedAtBadIrqlFsdSync</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975171">IoBuildSynchronousFsdRequestNoFree</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975173">IoBuildSynchronousFsdRequestWait</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975174">IoBuildSynchronousFsdRequestWaitTimeout</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975249">SignalEventInCompletion</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548257">IoAllocateIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548310">IoBuildAsynchronousFsdRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548318">IoBuildDeviceIoControlRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548343">IoCompleteRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552137">KeInitializeEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553350">KeWaitForSingleObject</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoBuildSynchronousFsdRequest routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
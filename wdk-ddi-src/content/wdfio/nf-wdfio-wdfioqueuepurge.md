---
UID: NF.wdfio.WdfIoQueuePurge
title: WdfIoQueuePurge
author: windows-driver-content
description: The WdfIoQueuePurge method causes the framework to stop queuing I/O requests to an I/O queue and to cancel unprocessed requests.
old-location: wdf\wdfioqueuepurge.htm
ms.assetid: bd6e9583-774f-4ca2-9c23-4d32b233daff
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfio.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfIoQueuePurge
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: ChangeQueueState, DriverCreate, EvtSurpriseRemoveNoSuspendQueue, KmdfIrql, KmdfIrql2, NoCancelFromEvtSurpriseRemove
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: WdfIoQueuePurge
req.iface: 
req.product: Windows 10 or later.
---

# WdfIoQueuePurge function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfIoQueuePurge</b> method causes the framework to stop queuing I/O requests to an I/O queue and to cancel unprocessed requests. </p>


## -syntax

````
VOID WdfIoQueuePurge(
  _In_     WDFQUEUE               Queue,
  _In_opt_ PFN_WDF_IO_QUEUE_STATE PurgeComplete,
  _In_opt_ WDFCONTEXT             Context
);
````


## -parameters
<dl>

### -param <i>Queue</i> [in]

<dd>
<p>A handle to a framework queue object.</p>
</dd>

### -param <i>PurgeComplete</i> [in, optional]

<dd>
<p>A pointer to a driver-supplied <a href="https://msdn.microsoft.com/14999036-c137-4056-b6f7-53a8476fd385">EvtIoQueueState</a> callback function. This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>Context</i> [in, optional]

<dd>
<p>An untyped pointer to driver-supplied context information that the framework passes to the <a href="https://msdn.microsoft.com/14999036-c137-4056-b6f7-53a8476fd385">EvtIoQueueState</a> callback function. This parameter is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p>None.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>After a driver calls <b>WdfIoQueuePurge</b>, the framework stops adding I/O requests to the specified queue. The framework <a href="wdf.canceling_i_o_requests">cancels</a> all requests that it has not delivered to the target device and calls the driver's  <a href="https://msdn.microsoft.com/7d3eb4d6-9fc7-4924-9b95-f5824713049b">CompletionRoutine</a> callback function  for each. The framework also attempts to cancel (by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff548338">IoCancelIrp</a>) any requests delivered to the target device that were not marked <a href="https://msdn.microsoft.com/0d561e0f-ca7e-44ed-9025-1a6513e4cd28">WDF_REQUEST_SEND_OPTION_IGNORE_TARGET_STATE</a>.</p>

<p>If the framework receives additional requests for the queue, it completes them with a completion status value of STATUS_INVALID_DEVICE_STATE.</p>

<p>If the driver supplies an <a href="https://msdn.microsoft.com/14999036-c137-4056-b6f7-53a8476fd385">EvtIoQueueState</a> callback function, the framework calls it after all requests that were delivered to the driver have been completed or canceled.</p>

<p>After a driver has purged an I/O queue, it can restart the queue by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff548478">WdfIoQueueStart</a>.</p>

<p>If the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550012">WdfRequestRequeue</a> after calling <b>WdfIoQueuePurge</b>, the requeue attempt may succeed before the purge is complete. In versions 1.9 and earlier of KMDF, this 
sequence causes the operating system to crash.  This problem is fixed in KMDF version 1.11 and later.</p>

<p>For more information about the <b>WdfIoQueuePurge</b> method, see <a href="wdf.managing_i_o_queues">Managing I/O Queues</a>.</p>

<p>The following code example purges an I/O queue and does not call a callback function when all requests that were delivered to the driver have been completed or canceled.</p>

<p>After a driver calls <b>WdfIoQueuePurge</b>, the framework stops adding I/O requests to the specified queue. The framework <a href="wdf.canceling_i_o_requests">cancels</a> all requests that it has not delivered to the target device and calls the driver's  <a href="https://msdn.microsoft.com/7d3eb4d6-9fc7-4924-9b95-f5824713049b">CompletionRoutine</a> callback function  for each. The framework also attempts to cancel (by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff548338">IoCancelIrp</a>) any requests delivered to the target device that were not marked <a href="https://msdn.microsoft.com/0d561e0f-ca7e-44ed-9025-1a6513e4cd28">WDF_REQUEST_SEND_OPTION_IGNORE_TARGET_STATE</a>.</p>

<p>If the framework receives additional requests for the queue, it completes them with a completion status value of STATUS_INVALID_DEVICE_STATE.</p>

<p>If the driver supplies an <a href="https://msdn.microsoft.com/14999036-c137-4056-b6f7-53a8476fd385">EvtIoQueueState</a> callback function, the framework calls it after all requests that were delivered to the driver have been completed or canceled.</p>

<p>After a driver has purged an I/O queue, it can restart the queue by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff548478">WdfIoQueueStart</a>.</p>

<p>If the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550012">WdfRequestRequeue</a> after calling <b>WdfIoQueuePurge</b>, the requeue attempt may succeed before the purge is complete. In versions 1.9 and earlier of KMDF, this 
sequence causes the operating system to crash.  This problem is fixed in KMDF version 1.11 and later.</p>

<p>For more information about the <b>WdfIoQueuePurge</b> method, see <a href="wdf.managing_i_o_queues">Managing I/O Queues</a>.</p>

<p>The following code example purges an I/O queue and does not call a callback function when all requests that were delivered to the driver have been completed or canceled.</p>

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
<dt>Wdfio.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.dll (UMDF)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975067">ChangeQueueState</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975076">EvtSurpriseRemoveNoSuspendQueue</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975093">NoCancelFromEvtSurpriseRemove</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547406">WdfIoQueueDrain</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548449">WdfIoQueuePurgeSynchronously</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/14999036-c137-4056-b6f7-53a8476fd385">EvtIoQueueState</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfIoQueuePurge method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
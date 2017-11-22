---
UID: NF.ks.KsFilterAttemptProcessing
title: KsFilterAttemptProcessing
author: windows-driver-content
description: The KsFilterAttemptProcessing function attempts to initiate processing on Filter.
old-location: stream\ksfilterattemptprocessing.htm
ms.assetid: 22c6bd15-98b7-4905-8551-c8202cc6840b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsFilterAttemptProcessing
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: KsFilterAttemptProcessing
req.iface: 
---

# KsFilterAttemptProcessing function



## -description
<p>The<b> KsFilterAttemptProcessing</b> function attempts to initiate processing on <i>Filter</i>.</p>


## -syntax

````
void KsFilterAttemptProcessing(
  _In_ PKSFILTER Filter,
  _In_ BOOLEAN   Asynchronous
);
````


## -parameters
<dl>

### -param <i>Filter</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff562522">KSFILTER</a> structure representing the AVStream filter object on which to attempt processing.</p>
</dd>

### -param <i>Asynchronous</i> [in]

<dd>
<p>This parameter contains an indication as to whether the processing dispatch should occur asynchronously or not (should it occur). An asynchronous dispatch is guaranteed if this is <b>TRUE</b>; however, synchronous processing dispatches are governed by conditions described below.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>If the minidriver calls <b>KsFilterAttemptProcessing</b> when all of the conditions required to process data are met, a processing dispatch occurs. For more information about the process callback, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff562554">KSFILTER_DISPATCH</a>. In order for the attempt to result in an actual dispatch, the filter's process control gate must be in an open state. Unlike pin-centric processing, filter-centric processing has many conditions that affect the process control gate. For more information about these requirements, see <a href="NULL">Filter-Centric Processing</a> and <a href="NULL">Pin-Centric Processing</a>.</p>

<p>If the process control gate is open, a processing dispatch occurs, either synchronously or asynchronously. If the caller specifies <b>TRUE</b> in the <i>Asynchronous</i> parameter, the processing dispatch always occurs asynchronously in a work item. However, if the caller requests a synchronous processing dispatch, the dispatch occurs synchronously only if the system is currently at an IRQL at which the minidriver can handle processing. If the system is at PASSIVE_LEVEL, the dispatch is guaranteed to happen synchronously. Conversely, if the system is at DISPATCH_LEVEL, the dispatch happens synchronously only if KSFILTER_FLAG_DISPATCH_LEVEL_PROCESSING is specified on the filter. Otherwise, a work item is queued to perform processing.</p>

<p>Note that this is only an attempt at processing; calling this function does not guarantee that processing will commence. Processing occurs only if the process control gate is "open." For more information, see <a href="NULL">Restarting Processing in AVStream</a> and <a href="NULL">Flow Control Gates in AVStream</a>.</p>

<p>If the minidriver calls <b>KsFilterAttemptProcessing</b> when all of the conditions required to process data are met, a processing dispatch occurs. For more information about the process callback, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff562554">KSFILTER_DISPATCH</a>. In order for the attempt to result in an actual dispatch, the filter's process control gate must be in an open state. Unlike pin-centric processing, filter-centric processing has many conditions that affect the process control gate. For more information about these requirements, see <a href="NULL">Filter-Centric Processing</a> and <a href="NULL">Pin-Centric Processing</a>.</p>

<p>If the process control gate is open, a processing dispatch occurs, either synchronously or asynchronously. If the caller specifies <b>TRUE</b> in the <i>Asynchronous</i> parameter, the processing dispatch always occurs asynchronously in a work item. However, if the caller requests a synchronous processing dispatch, the dispatch occurs synchronously only if the system is currently at an IRQL at which the minidriver can handle processing. If the system is at PASSIVE_LEVEL, the dispatch is guaranteed to happen synchronously. Conversely, if the system is at DISPATCH_LEVEL, the dispatch happens synchronously only if KSFILTER_FLAG_DISPATCH_LEVEL_PROCESSING is specified on the filter. Otherwise, a work item is queued to perform processing.</p>

<p>Note that this is only an attempt at processing; calling this function does not guarantee that processing will commence. Processing occurs only if the process control gate is "open." For more information, see <a href="NULL">Restarting Processing in AVStream</a> and <a href="NULL">Flow Control Gates in AVStream</a>.</p>

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
<p>Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562566">KSGATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562554">KSFILTER_DISPATCH</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562571">KsGateCaptureThreshold</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563494">KsPinAttemptProcessing</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsFilterAttemptProcessing function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.rxprocs.RxPurgeAllFobxs
title: RxPurgeAllFobxs
author: windows-driver-content
description: RxPurgeAllFobxs purges all of the FOBX structures associated with a network mini-redirector.
old-location: ifsk\rxpurgeallfobxs.htm
ms.assetid: 3d2a31be-1b59-48a8-8cde-61d7f7319724
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: rxprocs.h
req.include-header: Rxprocs.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxPurgeAllFobxs
req.alt-loc: rxprocs.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: RxPurgeAllFobxs
req.iface: 
req.product: Windows 10 or later.
---

# RxPurgeAllFobxs function



## -description
<p><b>RxPurgeAllFobxs</b> purges all of the FOBX structures associated with a network mini-redirector. </p>


## -syntax

````
VOID RxPurgeAllFobxs(
   PRDBSS_DEVICE_OBJECT RxDeviceObject
);
````


## -parameters
<dl>

### -param <i>RxDeviceObject</i> 

<dd>
<p>A pointer to the mini-redirector device object for which the purge should be done.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p>At cleanup, there are no more user handles associated with the file object. In such cases, the time window between close and cleanup is dictated by the additional references maintained by memory manager and cache manager. RDBSS uses a scavenger process running on a separate thread to scavenge and purge unneeded FOBX and other structures.</p>

<p>A network mini-redirector might call <b>RxPurgeAllFobxs</b> and <b>RxScavengeAllFobsx</b> in response to a PnP power change event. </p>

<p>The <b>RxPurgeAllFobxs</b> routine acquires the scavenger mutex, traverses the <b>ClosePendingFobxsList</b> member on the scavenger object removing list entries, and then releases the mutex. If the FOBX structure is not <b>NULL</b>,  <b>RxPurgeAllFobxs</b> will purge the FOBX structure and try to acquire an exclusive lock on the associated FCB structure. If successful, <b>RxPurgeAllFobxs</b> will then try to dereference the NET_FOBX structure and dereference, finalize, and release the FCB structure.</p>

<p>On checked builds, <b>RxPurgeAllFobxs</b> causes the system to ASSERT for a number of conditions including the following:</p>

<p>The <b>Flink</b> member of <i>RxScavenger-&gt;ClosePendingFobxsList</i> structure on the <b>RxDeviceObject</b> is <b>NULL</b>.</p>

<p><i>Fobx-&gt;NodeTypeCode</i> is not RDBSS_NTC_FOBX.</p>

<p>The <b>Flink</b> and <b>Blink</b> members for a list entry are <b>NULL</b>.</p>

<p>At cleanup, there are no more user handles associated with the file object. In such cases, the time window between close and cleanup is dictated by the additional references maintained by memory manager and cache manager. RDBSS uses a scavenger process running on a separate thread to scavenge and purge unneeded FOBX and other structures.</p>

<p>A network mini-redirector might call <b>RxPurgeAllFobxs</b> and <b>RxScavengeAllFobsx</b> in response to a PnP power change event. </p>

<p>The <b>RxPurgeAllFobxs</b> routine acquires the scavenger mutex, traverses the <b>ClosePendingFobxsList</b> member on the scavenger object removing list entries, and then releases the mutex. If the FOBX structure is not <b>NULL</b>,  <b>RxPurgeAllFobxs</b> will purge the FOBX structure and try to acquire an exclusive lock on the associated FCB structure. If successful, <b>RxPurgeAllFobxs</b> will then try to dereference the NET_FOBX structure and dereference, finalize, and release the FCB structure.</p>

<p>On checked builds, <b>RxPurgeAllFobxs</b> causes the system to ASSERT for a number of conditions including the following:</p>

<p>The <b>Flink</b> member of <i>RxScavenger-&gt;ClosePendingFobxsList</i> structure on the <b>RxDeviceObject</b> is <b>NULL</b>.</p>

<p><i>Fobx-&gt;NodeTypeCode</i> is not RDBSS_NTC_FOBX.</p>

<p>The <b>Flink</b> and <b>Blink</b> members for a list entry are <b>NULL</b>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Rxprocs.h (include Rxprocs.h)</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554679">RxPurgeRelatedFobxs</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554707">RxScavengeAllFobxs</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554713">RxScavengeFobxsForNetRoot</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxPurgeAllFobxs function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
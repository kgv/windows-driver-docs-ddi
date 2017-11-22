---
UID: NF.ks.KsCancelIo
title: KsCancelIo
author: windows-driver-content
description: The KsCancelIo function cancels all IRPs on the specified cancel list. If an IRP on the list does not have a cancel routine, only the cancel bit is set in the IRP. The function can be called at IRQ level DISPATCH_LEVEL or lower.
old-location: stream\kscancelio.htm
ms.assetid: 082a63d5-5ba5-4cd3-aea3-0184317e1e96
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsCancelIo
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
req.irql: < DISPATCH_LEVEL
ms.keywords: KsCancelIo
req.iface: 
---

# KsCancelIo function



## -description
<p>The <b>KsCancelIo</b> function cancels all IRPs on the specified cancel list. If an IRP on the list does not have a cancel routine, only the cancel bit is set in the IRP. The function can be called at IRQ level DISPATCH_LEVEL or lower.</p>


## -syntax

````
void KsCancelIo(
  _Inout_ PLIST_ENTRY QueueHead,
  _In_    PKSPIN_LOCK SpinLock
);
````


## -parameters
<dl>

### -param <i>QueueHead</i> [in, out]

<dd>
<p>Specifies the head of a driver-maintained queue containing the IRP's to be canceled.</p>
</dd>

### -param <i>SpinLock</i> [in]

<dd>
<p>Points to a caller-allocated spin lock for queue access. A copy of this pointer is kept in the IRP's KSQUEUE_SPINLOCK_IRP_STORAGE(Irp) for use by the cancel routine, if necessary.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>KsCancelIo </b>cancels all IRPs in a given driver-maintained queue. If the IRP has a cancel routine, the cancel routine is called. Otherwise, the cancel flag in the IRP is set to <b>TRUE</b>. The IRPs are not removed from the queue by this routine. It is the sole responsibility of the driver to ensure that the IRPs are removed either by the cancel routine specified in the IRP or by some other driver-supplied functionality.</p>

<p>If the IRP being canceled has a driver-supplied cancel routine, the cancel spin lock can be obtained from the IRP by calling KSQUEUE_SPINLOCK_IRP_STORAGE.</p>

<p><b>KsCancelIo </b>cancels all IRPs in a given driver-maintained queue. If the IRP has a cancel routine, the cancel routine is called. Otherwise, the cancel flag in the IRP is set to <b>TRUE</b>. The IRPs are not removed from the queue by this routine. It is the sole responsibility of the driver to ensure that the IRPs are removed either by the cancel routine specified in the IRP or by some other driver-supplied functionality.</p>

<p>If the IRP being canceled has a driver-supplied cancel routine, the cancel spin lock can be obtained from the IRP by calling KSQUEUE_SPINLOCK_IRP_STORAGE.</p>

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
<p>&lt; DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560934">KsAddIrpToCancelableQueue</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsCancelIo function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
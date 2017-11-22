---
UID: NF.rxtimer.RxCancelTimerRequest
title: RxCancelTimerRequest
author: windows-driver-content
description: RxCancelTimerRequest cancels a recurrent timer request. The request to be canceled is identified by the worker thread routine and associated context.
old-location: ifsk\rxcanceltimerrequest.htm
ms.assetid: b5aeb972-3e52-4cdc-842b-7848bb2f8dc7
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: rxtimer.h
req.include-header: Rxtimer.h, Rxworkq.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxCancelTimerRequest
req.alt-loc: rxtimer.h
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
ms.keywords: RxCancelTimerRequest
req.iface: 
req.product: Windows 10 or later.
---

# RxCancelTimerRequest function



## -description
<p><b>RxCancelTimerRequest</b> cancels a recurrent timer request. The request to be canceled is identified by the worker thread routine and associated context. </p>


## -syntax

````
NTSTATUS RxCancelTimerRequest(
  _In_ PRDBSS_DEVICE_OBJECT     pDeviceObject,
  _In_ PRX_WORKERTHREAD_ROUTINE Routine,
  _In_ PVOID                    pContext
);
````


## -parameters
<dl>

### -param <i>pDeviceObject</i> [in]

<dd>
<p>A pointer to the device object that initialized the timer. This parameter was passed to the <b>RxPostRecurrentTimerRequest</b> routine when this recurrent timer was initialized.</p>
</dd>

### -param <i>Routine</i> [in]

<dd>
<p>A pointer to the worker thread routine to call when this timer expires. This parameter was passed to the <b>RxPostRecurrentTimerRequest</b> routine when this recurrent timer was initialized.</p>
</dd>

### -param <i>pContext</i> [in]

<dd>
<p>A pointer to the context parameter that was passed to the <b>RxPostRecurrentTimerRequest</b> routine when this timer was initialized.</p>
</dd>
</dl>

## -returns
<p><b>RxCancelTimerRequest</b> returns STATUS_SUCCESS on success. </p>

## -remarks
<p>A recurrent timer is initialized by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff554615">RxPostRecurrentTimerRequest</a>.</p>

<p>If the recurrent timer is not found, this routine will return STATUS_NOT_FOUND.</p>

<p>A recurrent timer is initialized by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff554615">RxPostRecurrentTimerRequest</a>.</p>

<p>If the recurrent timer is not found, this routine will return STATUS_NOT_FOUND.</p>

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
<dt>Rxtimer.h (include Rxtimer.h or Rxworkq.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554612">RxPostOneShotTimerRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554615">RxPostRecurrentTimerRequest</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxCancelTimerRequest routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
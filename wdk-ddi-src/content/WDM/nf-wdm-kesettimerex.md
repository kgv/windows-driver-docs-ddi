---
UID: NF.wdm.KeSetTimerEx
title: KeSetTimerEx
author: windows-driver-content
description: The KeSetTimerEx routine sets the absolute or relative interval at which a timer object is to be set to a signaled state, optionally supplies a CustomTimerDpc routine to be executed when that interval expires, and optionally supplies a recurring interval for the timer.
old-location: kernel\kesettimerex.htm
ms.assetid: 9a2a092d-f9b5-42a2-9be4-bc934a9304fb
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
req.alt-api: KeSetTimerEx
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlKeDispatchLte, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL
ms.keywords: KeSetTimerEx
req.iface: 
req.product: Windows 10 or later.
---

# KeSetTimerEx function



## -description
<p>The <b>KeSetTimerEx</b> routine sets the absolute or relative interval at which a timer object is to be set to a signaled state, optionally supplies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff542983">CustomTimerDpc</a> routine to be executed when that interval expires, and optionally supplies a recurring interval for the timer.</p>


## -syntax

````
BOOLEAN KeSetTimerEx(
  _Inout_  PKTIMER       Timer,
  _In_     LARGE_INTEGER DueTime,
  _In_     LONG          Period,
  _In_opt_ PKDPC         Dpc
);
````


## -parameters
<dl>

### -param <i>Timer</i> [in, out]

<dd>
<p>Pointer to a timer object that was initialized with <a href="https://msdn.microsoft.com/library/windows/hardware/ff552168">KeInitializeTimer</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff552173">KeInitializeTimerEx</a>.</p>
</dd>

### -param <i>DueTime</i> [in]

<dd>
<p>Specifies the absolute or relative time at which the timer is to expire. If the value of the <i>DueTime</i> parameter is negative, the expiration time is relative to the current system time. Otherwise, the expiration time is absolute. The expiration time is expressed in system time units (100-nanosecond intervals). Absolute expiration times track any changes in the system time; relative expiration times are not affected by system time changes.</p>
</dd>

### -param <i>Period</i> [in]

<dd>
<p>Specifies an optional recurring interval for the timer in milliseconds. Must be a value that is greater than or equal to zero. If the value of this parameter is zero, the timer is a nonperiodic timer that does not automatically re-queue itself.</p>
</dd>

### -param <i>Dpc</i> [in, optional]

<dd>
<p>Pointer to a DPC object that was initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff552130">KeInitializeDpc</a>. This parameter is optional. </p>
</dd>
</dl>

## -returns
<p>If the timer object was already in the system timer queue, <b>KeSetTimerEx</b> returns <b>TRUE</b>.</p>

## -remarks
<p>The <b>KeSetTimerEx</b> routine does the following:</p>

<p>Computes the expiration time.</p>

<p>Sets the timer to a not-signaled state.</p>

<p>Sets the recurring interval for the timer, if one was specified.</p>

<p>Inserts the timer object in the system timer queue.</p>

<p>If the timer object was already in the timer queue, it is implicitly canceled before being set to the new expiration time. A call to <b>KeSetTimerEx</b> before the previously specified <i>DueTime</i> has expired cancels both the timer and the call to the <i>Dpc</i>, if any, associated with the previous call.</p>

<p>Expiration times are measured relative to the system clock, and the accuracy with which the operating system can detect when a timer expires is limited by the granularity of the system clock. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/jj602805">Timer Accuracy</a>.</p>

<p>If the <i>Dpc</i> parameter is specified, a DPC object is associated with the timer object. When the timer expires, the timer object is removed from the system timer queue and it is set to a signaled state. If a DPC object was associated with the timer when it was set, the DPC object is inserted in the system DPC queue to be executed as soon as conditions permit after the timer interval expires.</p>

<p>A DPC routine cannot deallocate a periodic timer. A DPC routine can deallocate a nonperiodic timer.</p>

<p>Note that a periodic timer is automatically restarted as soon as it expires. Thus, on a multiprocessor machine, the DPC for a periodic timer can be running on two processors simultaneously.</p>

<p>Only one instantiation of a given DPC object can be queued at any given moment. To avoid potential race conditions, the DPC passed to <b>KeSetTimerEx</b> should <u>not</u> be passed to <a href="https://msdn.microsoft.com/library/windows/hardware/ff552185">KeInsertQueueDpc</a>.</p>

<p>Drivers must cancel any active timers in their <a href="https://msdn.microsoft.com/library/windows/hardware/ff564886">Unload</a> routines. Use <a href="https://msdn.microsoft.com/library/windows/hardware/ff551970">KeCancelTimer</a> to cancel any timers.</p>

<p>For more information about timer objects, see <a href="https://msdn.microsoft.com/b58487de-6e9e-45f4-acb8-9233c8718ee2">Timer Objects and DPCs</a>.</p>

<p>The <b>KeSetTimerEx</b> routine does the following:</p>

<p>Computes the expiration time.</p>

<p>Sets the timer to a not-signaled state.</p>

<p>Sets the recurring interval for the timer, if one was specified.</p>

<p>Inserts the timer object in the system timer queue.</p>

<p>If the timer object was already in the timer queue, it is implicitly canceled before being set to the new expiration time. A call to <b>KeSetTimerEx</b> before the previously specified <i>DueTime</i> has expired cancels both the timer and the call to the <i>Dpc</i>, if any, associated with the previous call.</p>

<p>Expiration times are measured relative to the system clock, and the accuracy with which the operating system can detect when a timer expires is limited by the granularity of the system clock. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/jj602805">Timer Accuracy</a>.</p>

<p>If the <i>Dpc</i> parameter is specified, a DPC object is associated with the timer object. When the timer expires, the timer object is removed from the system timer queue and it is set to a signaled state. If a DPC object was associated with the timer when it was set, the DPC object is inserted in the system DPC queue to be executed as soon as conditions permit after the timer interval expires.</p>

<p>A DPC routine cannot deallocate a periodic timer. A DPC routine can deallocate a nonperiodic timer.</p>

<p>Note that a periodic timer is automatically restarted as soon as it expires. Thus, on a multiprocessor machine, the DPC for a periodic timer can be running on two processors simultaneously.</p>

<p>Only one instantiation of a given DPC object can be queued at any given moment. To avoid potential race conditions, the DPC passed to <b>KeSetTimerEx</b> should <u>not</u> be passed to <a href="https://msdn.microsoft.com/library/windows/hardware/ff552185">KeInsertQueueDpc</a>.</p>

<p>Drivers must cancel any active timers in their <a href="https://msdn.microsoft.com/library/windows/hardware/ff564886">Unload</a> routines. Use <a href="https://msdn.microsoft.com/library/windows/hardware/ff551970">KeCancelTimer</a> to cancel any timers.</p>

<p>For more information about timer objects, see <a href="https://msdn.microsoft.com/b58487de-6e9e-45f4-acb8-9233c8718ee2">Timer Objects and DPCs</a>.</p>

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547812">IrqlKeDispatchLte</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551970">KeCancelTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552130">KeInitializeDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552168">KeInitializeTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552173">KeInitializeTimerEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553099">KeReadStateTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553324">KeWaitForMultipleObjects</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553350">KeWaitForSingleObject</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeSetTimerEx routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
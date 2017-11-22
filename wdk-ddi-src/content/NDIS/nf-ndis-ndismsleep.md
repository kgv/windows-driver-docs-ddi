---
UID: NF.ndis.NdisMSleep
title: NdisMSleep
author: windows-driver-content
description: The NdisMSleep function delays execution of the caller for a given interval in microseconds.
old-location: netvista\ndismsleep.htm
ms.assetid: 5b6c3fc5-4220-4a4b-9412-8bfc8141ea90
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisMSleep (NDIS 5.1)) in Windows
   Vista. Supported for NDIS 5.1 drivers (see 
   NdisMSleep (NDIS 5.1)).
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMSleep
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Miniport_Driver_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: < DISPATCH_LEVEL
ms.keywords: NdisMSleep
req.iface: 
---

# NdisMSleep function



## -description
<p>The 
  <b>NdisMSleep</b> function delays execution of the caller for a given interval in microseconds.</p>


## -syntax

````
VOID NdisMSleep(
  _In_ ULONG MicrosecondsToSleep
);
````


## -parameters
<dl>

### -param <i>MicrosecondsToSleep</i> [in]

<dd>
<p>The number of microseconds to delay.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>For the given time in the 
    <i>MicrosecondsToSleep</i> parameter, the caller's thread of execution is put into a wait state, thereby
    allowing other threads to get work done on the current processor. When the given interval expires, the
    caller of 
    <b>NdisMSleep</b> resumes execution.</p>

<p>An NDIS driver should always call 
    <b>NdisMSleep</b> in preference to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564568">NdisStallExecution</a> function unless the
    driver is running at IRQL &gt;= DISPATCH_LEVEL. 
    <b>NdisMSleep</b> can accept a larger delay interval than 
    <b>NdisStallExecution</b>, which should 
    <u>never</u> be called with an interval greater than 50 microseconds. Do not call <b>NdisMSleep</b> with a timeout of more than 30,000,000 microseconds (that is, 30 seconds or half a minute).</p>

<p>Miniport drivers can call 
    <b>NdisMSleep</b> from their 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> and,
    possibly, 
    <a href="https://msdn.microsoft.com/b8d452b4-bef3-4991-87cf-fac15bedfde4">MiniportHaltEx</a> functions when either
    function must wait for state changes to occur in the NIC before that function continues its
    operations.</p>

<p>Both 
    <b>NdisMSleep</b> and 
    <b>NdisStallExecution</b> allow a miniport driver to specify a delay consistently and independently of the
    clock speed of the host CPU. Neither function involves a timer object such as those that are used by the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564563">NdisSetTimerObject</a> function. The
    resolution of the host system clock varies, so very short delays can take slightly longer than the delay
    time that the caller of 
    <b>NdisMSleep</b> or 
    <b>NdisStallExecution</b> specified.</p>

<p>For the given time in the 
    <i>MicrosecondsToSleep</i> parameter, the caller's thread of execution is put into a wait state, thereby
    allowing other threads to get work done on the current processor. When the given interval expires, the
    caller of 
    <b>NdisMSleep</b> resumes execution.</p>

<p>An NDIS driver should always call 
    <b>NdisMSleep</b> in preference to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564568">NdisStallExecution</a> function unless the
    driver is running at IRQL &gt;= DISPATCH_LEVEL. 
    <b>NdisMSleep</b> can accept a larger delay interval than 
    <b>NdisStallExecution</b>, which should 
    <u>never</u> be called with an interval greater than 50 microseconds. Do not call <b>NdisMSleep</b> with a timeout of more than 30,000,000 microseconds (that is, 30 seconds or half a minute).</p>

<p>Miniport drivers can call 
    <b>NdisMSleep</b> from their 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> and,
    possibly, 
    <a href="https://msdn.microsoft.com/b8d452b4-bef3-4991-87cf-fac15bedfde4">MiniportHaltEx</a> functions when either
    function must wait for state changes to occur in the NIC before that function continues its
    operations.</p>

<p>Both 
    <b>NdisMSleep</b> and 
    <b>NdisStallExecution</b> allow a miniport driver to specify a delay consistently and independently of the
    clock speed of the host CPU. Neither function involves a timer object such as those that are used by the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564563">NdisSetTimerObject</a> function. The
    resolution of the host system clock varies, so very short delays can take slightly longer than the delay
    time that the caller of 
    <b>NdisMSleep</b> or 
    <b>NdisStallExecution</b> specified.</p>

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
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff553640">NdisMSleep (NDIS 5.1)</a>) in Windows
   Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisMSleep (NDIS 5.1)</b>).</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547979">Irql_Miniport_Driver_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b8d452b4-bef3-4991-87cf-fac15bedfde4">MiniportHaltEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/76e59376-58a4-4e35-bac4-ec5938c88cd7">NetTimerCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564563">NdisSetTimerObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564568">NdisStallExecution</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564651">NdisWaitEvent</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMSleep function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
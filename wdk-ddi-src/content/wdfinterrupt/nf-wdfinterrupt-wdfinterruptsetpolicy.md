---
UID: NF.wdfinterrupt.WdfInterruptSetPolicy
title: WdfInterruptSetPolicy
author: windows-driver-content
description: The WdfInterruptSetPolicy method specifies the interrupt priority, processor affinity, and affinity policy for a specified interrupt.
old-location: wdf\wdfinterruptsetpolicy.htm
ms.assetid: f61bef13-d9b5-4e6a-8657-995a1fcbf7b1
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfinterrupt.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfInterruptSetPolicy
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfInterruptSetPolicy
req.iface: 
req.product: Windows 10 or later.
---

# WdfInterruptSetPolicy function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfInterruptSetPolicy</b> method specifies the interrupt priority, processor affinity, and affinity policy for a specified interrupt.</p>


## -syntax

````
VOID WdfInterruptSetPolicy(
  _In_ WDFINTERRUPT           Interrupt,
  _In_ WDF_INTERRUPT_POLICY   Policy,
  _In_ WDF_INTERRUPT_PRIORITY Priority,
  _In_ KAFFINITY              TargetProcessorSet
);
````


## -parameters
<dl>

### -param <i>Interrupt</i> [in]

<dd>
<p>A handle to a framework interrupt object.</p>
</dd>

### -param <i>Policy</i> [in]

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/hh464032">WDF_INTERRUPT_POLICY</a>-typed enumerator that specifies a processor affinity policy for the interrupt.</p>
</dd>

### -param <i>Priority</i> [in]

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff552355">WDF_INTERRUPT_PRIORITY</a>-typed enumerator that specifies a priority for the interrupt.</p>
</dd>

### -param <i>TargetProcessorSet</i> [in]

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff551830">KAFFINITY</a>-typed value that specifies a processor affinity for the interrupt, if the <i>Policy</i> parameter is set to <b>WdfIrqPolicySpecifiedProcessors</b>.</p>
</dd>
</dl>

## -returns
<p>None.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>Windows Vista and later versions of the operating system allow drivers to specify an interrupt's priority, processor affinity, and affinity policy. For information about how to use the registry to override the values that <b>WdfInterruptSetPolicy</b> sets, see <a href="https://msdn.microsoft.com/e36a52d0-3a94-4017-b4a1-0b41f737523c">Interrupt Affinity and Priority</a>.</p>

<p>If a driver is running on an operating system version that is earlier than Windows Vista, the framework ignores the values that the driver specifies when it calls <b>WdfInterruptSetPolicy</b>.</p>

<p>For more information about registry values and INF sections that specify an interrupt's priority, processor affinity, and affinity policy, see <a href="https://msdn.microsoft.com/e36a52d0-3a94-4017-b4a1-0b41f737523c">Interrupt Affinity and Priority</a>.</p>

<p>If a driver calls <b>WdfInterruptSetPolicy</b>, it typically does so in its <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function, after calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff547345">WdfInterruptCreate</a>.</p>

<p>If your driver creates interrupts in <a href="https://msdn.microsoft.com/a3d4a983-8a75-44be-bd72-8673d89f9f87">EvtDevicePrepareHardware</a>, do not use <b>WdfInterruptSetPolicy</b> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547381">WdfInterruptSetExtendedPolicy</a>. Instead, apply policy in <a href="https://msdn.microsoft.com/7d9b38b5-989d-45a3-8771-57a8d1f98725">EvtDeviceFilterAddResourceRequirements</a>, by directly manipulating the interrupt resource requirement that this callback function receives in its <i>IoResourceRequirementsList</i> parameter.</p>

<p>For more information about handling interrupts in framework-based drivers, see <a href="wdf.handling_hardware_interrupts">Handling Hardware Interrupts</a>.</p>

<p>The following code example assigns a device interrupt to processor 0, with normal priority.</p>

<p>Windows Vista and later versions of the operating system allow drivers to specify an interrupt's priority, processor affinity, and affinity policy. For information about how to use the registry to override the values that <b>WdfInterruptSetPolicy</b> sets, see <a href="https://msdn.microsoft.com/e36a52d0-3a94-4017-b4a1-0b41f737523c">Interrupt Affinity and Priority</a>.</p>

<p>If a driver is running on an operating system version that is earlier than Windows Vista, the framework ignores the values that the driver specifies when it calls <b>WdfInterruptSetPolicy</b>.</p>

<p>For more information about registry values and INF sections that specify an interrupt's priority, processor affinity, and affinity policy, see <a href="https://msdn.microsoft.com/e36a52d0-3a94-4017-b4a1-0b41f737523c">Interrupt Affinity and Priority</a>.</p>

<p>If a driver calls <b>WdfInterruptSetPolicy</b>, it typically does so in its <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function, after calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff547345">WdfInterruptCreate</a>.</p>

<p>If your driver creates interrupts in <a href="https://msdn.microsoft.com/a3d4a983-8a75-44be-bd72-8673d89f9f87">EvtDevicePrepareHardware</a>, do not use <b>WdfInterruptSetPolicy</b> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff547381">WdfInterruptSetExtendedPolicy</a>. Instead, apply policy in <a href="https://msdn.microsoft.com/7d9b38b5-989d-45a3-8771-57a8d1f98725">EvtDeviceFilterAddResourceRequirements</a>, by directly manipulating the interrupt resource requirement that this callback function receives in its <i>IoResourceRequirementsList</i> parameter.</p>

<p>For more information about handling interrupts in framework-based drivers, see <a href="wdf.handling_hardware_interrupts">Handling Hardware Interrupts</a>.</p>

<p>The following code example assigns a device interrupt to processor 0, with normal priority.</p>

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
<dt>Wdfinterrupt.h (include Wdf.h)</dt>
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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547345">WdfInterruptCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547381">WdfInterruptSetExtendedPolicy</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfInterruptSetPolicy method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
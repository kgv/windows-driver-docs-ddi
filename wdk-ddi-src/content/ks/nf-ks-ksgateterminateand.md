---
UID: NF.ks.KsGateTerminateAnd
title: KsGateTerminateAnd
author: windows-driver-content
description: The KsGateTerminateAnd function deletes an existing AND gate and removes an input from any attached OR gate.
old-location: stream\ksgateterminateand.htm
ms.assetid: 3f29fb48-5145-4b2c-8a0c-3130f4491675
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsGateTerminateAnd
req.alt-loc: ks.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level
ms.keywords: KsGateTerminateAnd
req.iface: 
---

# KsGateTerminateAnd function



## -description
<p>The<b> KsGateTerminateAnd</b> function deletes an existing AND gate and removes an input from any attached OR gate.</p>


## -syntax

````
void __inline KsGateTerminateAnd(
  _In_ PKSGATE AndGate
);
````


## -parameters
<dl>

### -param <i>AndGate</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff562566">KSGATE</a> structure that is the AND gate to delete. This gate must be at the beginning of a gate chain.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Logical gates should be deleted in a front to back manner. <b>KsGateTerminateAnd</b> does not update the gate chain for gates that are deleted at the end or in the middle. For more information, see <a href="NULL">Flow Control Gates in AVStream</a>. </p>

<p>Logical gates should be deleted in a front to back manner. <b>KsGateTerminateAnd</b> does not update the gate chain for gates that are deleted at the end or in the middle. For more information, see <a href="NULL">Flow Control Gates in AVStream</a>. </p>

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
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562574">KsGateInitializeAnd</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562576">KsGateInitializeOr</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562588">KsGateTerminateOr</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsGateTerminateAnd function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
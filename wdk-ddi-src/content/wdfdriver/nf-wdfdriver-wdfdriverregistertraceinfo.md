---
UID: NF.wdfdriver.WdfDriverRegisterTraceInfo
title: WdfDriverRegisterTraceInfo
author: windows-driver-content
description: The WdfDriverRegisterTraceInfo method is reserved for internal use only.
old-location: wdf\wdfdriverregistertraceinfo.htm
ms.assetid: f2d332cd-d744-444c-b616-d8400ad30d43
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdriver.h
req.include-header: Wdf.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WdfDriverRegisterTraceInfo
req.alt-loc: Wdfdriver.h
req.ddi-compliance: DriverCreate
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Not applicable
ms.keywords: WdfDriverRegisterTraceInfo
req.iface: 
req.product: Windows 10 or later.
---

# WdfDriverRegisterTraceInfo function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDriverRegisterTraceInfo</b> method is reserved for internal use only.</p>


## -syntax

````
NTSTATUS WdfDriverRegisterTraceInfo(
  _In_ PDRIVER_OBJECT         DriverObject,
  _In_ PFN_WDF_TRACE_CALLBACK EvtTraceCallback,
  _In_ PVOID                  ControlBlock
);
````


## -parameters
<dl>

### -param <i>DriverObject</i> [in]

<dd></dd>

### -param <i>EvtTraceCallback</i> [in]

<dd></dd>

### -param <i>ControlBlock</i> [in]

<dd></dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfdriver.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Not applicable</p>
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
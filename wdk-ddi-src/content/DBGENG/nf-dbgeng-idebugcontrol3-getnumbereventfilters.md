---
UID: NF.dbgeng.IDebugControl3.GetNumberEventFilters
title: IDebugControl3::GetNumberEventFilters
author: windows-driver-content
description: The GetNumberEventFilters method returns the number of event filters currently used by the engine.
old-location: debugger\getnumbereventfilters.htm
ms.assetid: 6bb80c64-bb2e-4388-b1a8-479bdaa8b635
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugControl.GetNumberEventFilters,IDebugControl2.GetNumberEventFilters,IDebugControl3.GetNumberEventFilters
req.alt-loc: dbgeng.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: IDebugControl3, GetNumberEventFilters, IDebugControl3::GetNumberEventFilters
req.iface: IDebugControl3
---

# IDebugControl3::GetNumberEventFilters method



## -description
<p>The <b>GetNumberEventFilters</b> method returns the number of <a href="debugger.events#event_filters#event_filters">event filters</a> currently used by the engine.</p>


## -syntax

````
HRESULT GetNumberEventFilters(
  [out] PULONG SpecificEvents,
  [out] PULONG SpecificExceptions,
  [out] PULONG ArbitraryExceptions
);
````


## -parameters
<dl>

### -param <i>SpecificEvents</i> [out]

<dd>
<p>Receives the number of <a href="debugger.events#events#events">events</a> that can be controlled using the specific event filters.  These events are enumerated using some of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541490">DEBUG_FILTER_XXX</a> constants.</p>
</dd>

### -param <i>SpecificExceptions</i> [out]

<dd>
<p>Receives the number of <a href="wdkgloss.e#wdkgloss.exception#wdkgloss.exception"><i>exceptions</i></a> that can be controlled using the specific exception filters.  The first specific exception filter is the default exception filter.  The exceptions controlled by the other specific exception filters will always have their own filter and will not inherit their behavior from the default specific exception filter.  These exception filters are identified by their exception code.  See <a href="https://msdn.microsoft.com/library/windows/hardware/ff558784">Specific Exceptions</a> for a list of the specific exception filters.</p>
</dd>

### -param <i>ArbitraryExceptions</i> [out]

<dd>
<p>Receives the number of arbitrary exception filters currently used by the engine.  These exception filters are identified by their exception code.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

## -remarks
<p>For more information about event filters, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff543071">Event Filters</a>.</p>

<p>For more information about event filters, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff543071">Event Filters</a>.</p>

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
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>
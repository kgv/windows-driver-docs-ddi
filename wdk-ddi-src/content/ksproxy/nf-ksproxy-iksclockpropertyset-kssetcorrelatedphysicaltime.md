---
UID: NF.ksproxy.IKsClockPropertySet.KsSetCorrelatedPhysicalTime
title: IKsClockPropertySet::KsSetCorrelatedPhysicalTime
author: windows-driver-content
description: The KsSetCorrelatedPhysicalTime method sets the physical time with the correlated system time on the underlying clock.
old-location: stream\iksclockpropertyset_kssetcorrelatedphysicaltime.htm
ms.assetid: 208fecc5-f01f-41f3-80d3-d811b3f4173a
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ksproxy.h
req.include-header: Ksproxy.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IKsClockPropertySet.KsSetCorrelatedPhysicalTime
req.alt-loc: ksproxy.h
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
ms.keywords: IKsClockPropertySet, KsSetCorrelatedPhysicalTime, IKsClockPropertySet::KsSetCorrelatedPhysicalTime
req.iface: IKsClockPropertySet
---

# IKsClockPropertySet::KsSetCorrelatedPhysicalTime method



## -description
<p>The <b>KsSetCorrelatedPhysicalTime</b> method sets the physical time with the correlated system time on the underlying clock. </p>


## -syntax

````
HRESULT KsSetCorrelatedPhysicalTime(
  [in] KSCORRELATED_TIME *CorrelatedTime
);
````


## -parameters
<dl>

### -param <i>CorrelatedTime</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561033">KSCORRELATED_TIME</a> structure that contains the physical clock time along with the correlated system time to which to set the underlying clock. </p>
</dd>
</dl>

## -returns
<p>Returns NOERROR if successful; otherwise, returns an error code.</p>

## -remarks
<p>The proxy uses the <a href="https://msdn.microsoft.com/library/windows/hardware/ff564461">KSPROPERTY_CLOCK_CORRELATEDPHYSICALTIME</a> property to set the correlated time. </p>

<p>The proxy uses the <a href="https://msdn.microsoft.com/library/windows/hardware/ff564461">KSPROPERTY_CLOCK_CORRELATEDPHYSICALTIME</a> property to set the correlated time. </p>

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
<dt>Ksproxy.h (include Ksproxy.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559733">IKsClockPropertySet::KsGetCorrelatedPhysicalTime</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561033">KSCORRELATED_TIME</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564461">KSPROPERTY_CLOCK_CORRELATEDPHYSICALTIME</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20IKsClockPropertySet::KsSetCorrelatedPhysicalTime method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
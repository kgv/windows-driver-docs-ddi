---
UID: NF.ks.KsFilterFactoryGetNextSiblingFilterFactory
title: KsFilterFactoryGetNextSiblingFilterFactory
author: windows-driver-content
description: The KsFilterFactoryGetNextSiblingFilterFactory function returns the next filter factory belonging to the parent device of FilterFactory.
old-location: stream\ksfilterfactorygetnextsiblingfilterfactory.htm
ms.assetid: e397d36c-3f28-4a70-9b4a-f13be094d47b
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
req.alt-api: KsFilterFactoryGetNextSiblingFilterFactory
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
req.irql: PASSIVE_LEVEL
ms.keywords: KsFilterFactoryGetNextSiblingFilterFactory
req.iface: 
---

# KsFilterFactoryGetNextSiblingFilterFactory function



## -description
<p>The<b> KsFilterFactoryGetNextSiblingFilterFactory</b> function returns the next filter factory belonging to the parent device of <i>FilterFactory</i>.</p>


## -syntax

````
PKSFILTERFACTORY __inline KsFilterFactoryGetNextSiblingFilterFactory(
  _In_ PKSFILTERFACTORY FilterFactory
);
````


## -parameters
<dl>

### -param <i>FilterFactory</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562530">KSFILTERFACTORY</a> for which to return the next filter factory of its parent device.</p>
</dd>
</dl>

## -returns
<p><b>KsFilterFactoryGetNextSiblingFilterFactory</b> returns a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff562530">KSFILTERFACTORY</a> structure that represents the next sibling filter factory of <i>FilterFactory</i>. If no such filter factory exists, <b>NULL</b> is returned.</p>

## -remarks
<p>This call is an inline function call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff562643">KsGetNextSibling</a>. Note that the object hierarchy is guaranteed to be stable only while the appropriate mutex is held, in this case the device mutex. For more information, see <a href="NULL">Mutexes in AVStream</a>.</p>

<p>This call is an inline function call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff562643">KsGetNextSibling</a>. Note that the object hierarchy is guaranteed to be stable only while the appropriate mutex is held, in this case the device mutex. For more information, see <a href="NULL">Mutexes in AVStream</a>.</p>

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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562530">KSFILTERFACTORY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561684">KsDeviceGetFirstChildFilterFactory</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562643">KsGetNextSibling</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsFilterFactoryGetNextSiblingFilterFactory function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
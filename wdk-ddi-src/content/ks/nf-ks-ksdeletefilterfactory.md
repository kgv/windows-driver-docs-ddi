---
UID: NF.ks.KsDeleteFilterFactory
title: KsDeleteFilterFactory
author: windows-driver-content
description: KsDeleteFilterFactory deletes a given filter factory.
old-location: stream\ksdeletefilterfactory.htm
ms.assetid: 4d946524-8ad2-45a0-91be-861b30b0c297
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
req.alt-api: KsDeleteFilterFactory
req.alt-loc: Ks.h
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
ms.keywords: KsDeleteFilterFactory
req.iface: 
---

# KsDeleteFilterFactory function



## -description
<p><b>KsDeleteFilterFactory</b> deletes a given filter factory.</p>


## -syntax

````
NTSTATUS KsDeleteFilterFactory(
  _In_ PKSFILTERFACTORY FilterFactory
);
````


## -parameters
<dl>

### -param <i>FilterFactory</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff562530">KSFILTERFACTORY</a> structure that represents the filter factory to be deleted.</p>
</dd>
</dl>

## -returns
<p>STATUS_SUCCESS is returned if the filter factory was able to be deleted. Otherwise, an appropriate error code is returned.</p>

## -remarks


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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561650">KsCreateFilterFactory</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562531">KsFilterFactoryAddCreateItem</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562539">KsFilterFactorySetDeviceClassesState</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562530">KSFILTERFACTORY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsDeleteFilterFactory function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
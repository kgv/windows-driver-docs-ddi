---
UID: NF.ks.KsReleaseCachedMdl
title: KsReleaseCachedMdl
author: windows-driver-content
description: The KsReleaseCachedMdl function is used to release the MDL acquired by the KsAcquireCachedMdl call.
old-location: stream\ksreleasecachedmdl.htm
ms.assetid: 8EDBD8FF-6417-44C0-87C0-14D71FEFA380
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsReleaseCachedMdl
req.alt-loc: ks.lib,ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: 
ms.keywords: KsReleaseCachedMdl
req.iface: 
---

# KsReleaseCachedMdl function



## -description
<p>The <b>KsReleaseCachedMdl</b> function is used to release the MDL acquired by the <a href="https://msdn.microsoft.com/library/windows/hardware/mt186387">KsAcquireCachedMdl</a> call.</p>


## -syntax

````
void _Must_inspect_result_ _IRQL_requires_max_(PASSIVE_LEVEL) KSDDKAPI NTSTATUS WINAPI KsReleaseCachedMdl(
  _In_ REFGUID Guid,
  _In_ PMDL    MdlAddr,
  _In_ HANDLE  ReleaseContext
);
````


## -parameters
<dl>

### -param <i>Guid</i> [in]

<dd>
<p>The GUID extracted from the <b>MFSampleExtension_MDLCacheCookie</b> attribute item of the <b>IMFSample</b> passed by the pipeline.</p>
</dd>

### -param <i>MdlAddr</i> [in]

<dd>
<p>MDL address retrieved in the <a href="https://msdn.microsoft.com/library/windows/hardware/mt186387">KsAcquireCachedMdl</a> call. This should not be touched after the <b>KsReleaseCachedMdl</b> call.</p>
</dd>

### -param <i>ReleaseContext</i> [in]

<dd>
<p>The context passed as an output in the <a href="https://msdn.microsoft.com/library/windows/hardware/mt186387">KsAcquireCachedMdl</a> call.</p>
</dd>
</dl>

## -returns
<p>Returns <b>STATUS_SUCCESS</b> for success conditions.</p>

## -remarks


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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
</dl>
</td>
</tr>
</table>
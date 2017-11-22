---
UID: NF.ks.KsQueryObjectCreateItem
title: KsQueryObjectCreateItem
author: windows-driver-content
description: The KsQueryObjectCreateItem function returns the create item assigned to the object when created.
old-location: stream\ksqueryobjectcreateitem.htm
ms.assetid: dd6d436c-6166-4baf-b180-67f7aa7238e3
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsQueryObjectCreateItem
req.alt-loc: Ks.lib,Ks.dll
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
ms.keywords: KsQueryObjectCreateItem
req.iface: 
---

# KsQueryObjectCreateItem function



## -description
<p>The <b>KsQueryObjectCreateItem</b> function returns the create item assigned to the object when created.</p>


## -syntax

````
PKSOBJECT_CREATE_ITEM KsQueryObjectCreateItem(
  _In_ KSOBJECT_HEADER Header
);
````


## -parameters
<dl>

### -param <i>Header</i> [in]

<dd>
<p>Indicates the header previously allocated.</p>
</dd>
</dl>

## -returns
<p>The <b>KsQueryObjectCreateItem</b> function returns a pointer to a create item.</p>

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
<dt>Ks.h (include Ks.h)</dt>
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
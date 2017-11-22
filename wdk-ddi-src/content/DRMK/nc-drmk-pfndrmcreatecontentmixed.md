---
UID: NC.drmk.PFNDRMCREATECONTENTMIXED
title: PFNDRMCREATECONTENTMIXED
author: windows-driver-content
description: This callback function is reserved for system use.
old-location: audio\pfndrmcreatecontentmixed.htm
ms.assetid: A4BA818F-126F-4134-AEDA-F983ADFC4A07
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: audio
req.header: drmk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DRMCreateContentMixed
req.alt-loc: Drmk.h
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
ms.keywords: WDI_TXRX_TARGET_CONFIGURATION, WDI_TXRX_TARGET_CONFIGURATION, *PWDI_TXRX_TARGET_CONFIGURATION
req.iface: 
---

# PFNDRMCREATECONTENTMIXED callback



## -description
<p>This callback function is reserved for system use.</p>


## -prototype

````
PFNDRMCREATECONTENTMIXED DRMCreateContentMixed;

NTSTATUS DRMCreateContentMixed(
  _In_  PULONG paContentId,
  _In_  ULONG  cContentId,
  _Out_ PULONG pMixedContentId
)
{ ... }

typedef PFNDRMCREATECONTENTMIXED DRMCreateContentMixed;
````


## -parameters
<dl>

### -param <i>paContentId</i> [in]

<dd>
<p>This parameter is reserved for system use.</p>
</dd>

### -param <i>cContentId</i> [in]

<dd>
<p>This parameter is reserved for system use.</p>
</dd>

### -param <i>pMixedContentId</i> [out]

<dd>
<p>This parameter is reserved for system use.</p>
</dd>
</dl>

## -returns
<p>This return value is reserved for system use.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Drmk.h</dt>
</dl>
</td>
</tr>
</table>
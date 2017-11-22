---
UID: NF.rilapi.RIL_Dial
title: RIL_Dial
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\ril_dial.htm
ms.assetid: 755a834b-6590-4289-99b1-058690c1ad4f
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: rilapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RIL_Dial
req.alt-loc: rilapi.h
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
ms.keywords: RIL_Dial
req.iface: 
req.product: Windows 10 or later.
---

# RIL_Dial function



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 

            </p>


## -syntax

````
HRESULT  RIL_Dial(
   HRIL                               hRil,
   LPVOID                             lpContext,
   DWORD                              dwExecutor,
   const RILADDRESS                   lpraAddress,
   DWORD                              dwOptions,
   RILCALLTYPE                        dwType,
   const LPRILCALLMEDIAOFFERANSWERSET lprcmOfferAnswer
);
````


## -parameters
<dl>

### -param <i>hRil</i> 

<dd></dd>

### -param <i>lpContext</i> 

<dd></dd>

### -param <i>dwExecutor</i> 

<dd></dd>

### -param <i>lpraAddress</i> 

<dd></dd>

### -param <i>dwOptions</i> 

<dd></dd>

### -param <i>dwType</i> 

<dd></dd>

### -param <i>lprcmOfferAnswer</i> 

<dd></dd>
</dl>

## -returns
<p>If this method succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Rilapi.h</dt>
</dl>
</td>
</tr>
</table>
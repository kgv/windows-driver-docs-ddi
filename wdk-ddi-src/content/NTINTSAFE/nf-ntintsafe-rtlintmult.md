---
UID: NF.ntintsafe.RtlIntMult
title: RtlIntMult
author: windows-driver-content
description: Multiplies one value of type INT by another.
old-location: kernel\rtlintmult.htm
ms.assetid: 5417D6B1-0523-4C01-9C07-571D096E10F3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntintsafe.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlIntMult
req.alt-loc: Ntintsafe.h
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
ms.keywords: RtlIntMult
req.iface: 
---

# RtlIntMult function



## -description
<p>Multiplies one value of type <b>INT</b> by another.</p>


## -syntax

````
NTSTATUS RtlIntMult(
  _In_  INT iMultiplicand,
  _In_  INT iMultiplier,
  _Out_ INT *piResult
);
````


## -parameters
<dl>

### -param <i>iMultiplicand</i> [in]

<dd>
<p>The value to be multiplied by <i>iMultiplier</i>.</p>
</dd>

### -param <i>iMultiplier</i> [in]

<dd>
<p>The value by which to multiply <i>iMultiplicand</i>.</p>
</dd>

### -param <i>piResult</i> [out]

<dd>
<p>A pointer to the result. If the operation results in a value that overflows or underflows the capacity of the type, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide arithmetic operations and perform validity checks with minimal impact on performance.</p>

<p>This function uses the following alternate name:</p>

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
<dt>Ntintsafe.h</dt>
</dl>
</td>
</tr>
</table>
---
UID: NF.ntintsafe.RtlIntPtrAdd
title: RtlIntPtrAdd
author: windows-driver-content
description: Adds two values of type INT_PTR.
old-location: kernel\rtlintptradd.htm
ms.assetid: 97873113-7B0B-4121-B074-5B73D59489F4
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
req.alt-api: RtlIntPtrAdd
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
ms.keywords: RtlIntPtrAdd
req.iface: 
---

# RtlIntPtrAdd function



## -description
<p>Adds two values of type <b>INT_PTR</b>.</p>


## -syntax

````
NTSTATUS RtlIntPtrAdd(
  _In_  INT_PTR iAugend,
  _In_  INT_PTR iAddend,
  _Out_ INT_PTR *piResult
);
````


## -parameters
<dl>

### -param <i>iAugend</i> [in]

<dd>
<p>The first value in the equation.</p>
</dd>

### -param <i>iAddend</i> [in]

<dd>
<p>The value to add to <i>iAugend</i>.</p>
</dd>

### -param <i>piResult</i> [out]

<dd>
<p>A pointer to the sum. If the operation results in a value that overflows or underflows the capacity of the type, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide arithmetic operations and perform validity checks with minimal impact on performance.</p>

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
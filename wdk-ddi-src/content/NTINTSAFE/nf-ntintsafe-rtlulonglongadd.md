---
UID: NF.ntintsafe.RtlULongLongAdd
title: RtlULongLongAdd
author: windows-driver-content
description: Adds two values of type ULONGLONG.
old-location: kernel\rtlulonglongadd.htm
ms.assetid: AE58D20E-25A0-4D45-9E60-38EF2F1D1EF3
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
req.alt-api: RtlULongLongAdd
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
ms.keywords: RtlULongLongAdd
req.iface: 
---

# RtlULongLongAdd function



## -description
<p>Adds two values of type <b>ULONGLONG</b>.</p>


## -syntax

````
NTSTATUS RtlULongLongAdd(
  _In_  ULONGLONG ullAugend,
  _In_  ULONGLONG ullAddend,
  _Out_ ULONGLONG *pllResult
);
````


## -parameters
<dl>

### -param <i>ullAugend</i> [in]

<dd>
<p>The first value in the equation.</p>
</dd>

### -param <i>ullAddend</i> [in]

<dd>
<p>The value to add to <i>ullAugend</i>.</p>
</dd>

### -param <i>pllResult</i> [out]

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
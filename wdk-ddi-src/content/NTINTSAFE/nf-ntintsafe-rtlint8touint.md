---
UID: NF.ntintsafe.RtlInt8ToUInt
title: RtlInt8ToUInt
author: windows-driver-content
description: Converts a value of type INT8 to a value of type UINT.
old-location: kernel\rtlint8touint.htm
ms.assetid: 00C37CB5-4CBC-48C3-8D90-F01BF82E2EF6
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
req.alt-api: RtlInt8ToUInt
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
ms.keywords: RtlInt8ToUInt
req.iface: 
---

# RtlInt8ToUInt function



## -description
<p>Converts a value of type <b>INT8</b> to a value of type <b>UINT</b>.</p>


## -syntax

````
NTSTATUS RtlInt8ToUInt(
  _In_  INT8 i8Operand,
  _Out_ UINT *puResult
);
````


## -parameters
<dl>

### -param <i>i8Operand</i> [in]

<dd>
<p>The value to be converted.</p>
</dd>

### -param <i>puResult</i> [out]

<dd>
<p>A pointer to the converted value. In the case where the conversion causes a truncation of the original value, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide type conversions and perform validity checks with minimal impact on performance.</p>

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
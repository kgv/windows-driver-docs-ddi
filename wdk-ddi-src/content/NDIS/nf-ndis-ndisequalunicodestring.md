---
UID: NF.ndis.NdisEqualUnicodeString
title: NdisEqualUnicodeString
author: windows-driver-content
description: The NdisEqualUnicodeString function compares two Unicode strings and returns whether they are equal.
old-location: netvista\ndisequalunicodestring.htm
ms.assetid: 8f3abf40-bb47-4fa6-862b-6126edb00b36
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported for existing drivers in  NDIS 6.0 and later, but new drivers should use RtlEqualUnicodeString instead.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisEqualUnicodeString
req.alt-loc: ndis.h
req.ddi-compliance: Irql_Miscellaneous_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisEqualUnicodeString
req.iface: 
---

# NdisEqualUnicodeString function



## -description
<p>The
  <b>NdisEqualUnicodeString</b> function compares two Unicode strings and returns whether they are
  equal.</p>


## -syntax

````
BOOLEAN NdisEqualUnicodeString(
  _In_ PNDIS_STRING String1,
  _In_ PNDIS_STRING String2,
  _In_ BOOLEAN      CaseInSensitive
);
````


## -parameters
<dl>

### -param <i>String1</i> [in]

<dd>
<p>A pointer to an NDIS_STRING type that describes the first Unicode string.</p>
</dd>

### -param <i>String2</i> [in]

<dd>
<p>A pointer to an NDIS_STRING type that describes the second Unicode string.</p>
</dd>

### -param <i>CaseInSensitive</i> [in]

<dd>
<p>A Boolean value that is <b>TRUE</b>, if case should be ignored when doing the comparison. Otherwise, it
     is <b>FALSE</b>.</p>
</dd>
</dl>

## -returns
<p><b>NdisEqualUnicodeString</b> returns <b>TRUE</b> if the two Unicode strings are equal.</p>

## -remarks
<p>Starting with Windows 2000 and later drivers, a string of type NDIS_STRING is a counted,
    null-terminated Unicode string. That is, NDIS defines the NDIS_STRING type as a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> type.</p>

<p>Starting with Windows 2000 and later drivers, a string of type NDIS_STRING is a counted,
    null-terminated Unicode string. That is, NDIS defines the NDIS_STRING type as a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> type.</p>

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
<p>Supported for existing drivers in  NDIS 6.0 and later, but new drivers should use <a href="https://msdn.microsoft.com/library/windows/hardware/ff561854">RtlEqualUnicodeString</a> instead.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547982">Irql_Miscellaneous_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisEqualUnicodeString function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
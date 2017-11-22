---
UID: NS.d3d10umddi.D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT
title: D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT
author: windows-driver-content
description: Contains a response from the QueryAuthenticatedChannel(D3D11_1) function.
old-location: display\d3d11_1ddi_authenticated_query_output.htm
ms.assetid: 1e5d5b29-ecda-48be-b4fe-e3a153f2e0e2
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT
req.alt-loc: D3d10umddi.h
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
ms.keywords: D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT, D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT
req.iface: 
---

# D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT structure



## -description
<p>Contains a response from the <a href="https://msdn.microsoft.com/bb152e3d-497f-4798-86cc-6f300e24a05c">QueryAuthenticatedChannel(D3D11_1)</a> function.</p>


## -syntax

````
typedef struct D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT {
  D3D11_1DDI_OMAC omac;
  GUID            QueryType;
  HANDLE          hChannel;
  UINT            SequenceNumber;
  HRESULT         ReturnCode;
} D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT;
````


## -struct-fields
<dl>

### -field <b>omac</b>

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/hh406450">D3D11_1DDI_OMAC</a> structure that contains a Message Authentication Code (MAC) of the data. The driver uses Advanced Encryption Standard (AES)-based one-key CBC MAC (OMAC) to calculate this value for the block of data that appears after this structure member.</p>
</dd>

### -field <b>QueryType</b>

<dd>
<p>A GUID that specifies the query. For a list of possible values, see the <a href="https://msdn.microsoft.com/library/windows/hardware/hh406399">D3D11_1DDI_AUTHENTICATED_QUERY_INPUT</a> structure.</p>
</dd>

### -field <b>hChannel</b>

<dd>
<p>A handle to the authenticated channel. This handle was created through a call to the <a href="https://msdn.microsoft.com/90b43bc3-6569-4799-8be3-e4e60f59164f">CreateAuthenticatedChannel(D3D11_1)</a> function.</p>
</dd>

### -field <b>SequenceNumber</b>

<dd>
<p>The query sequence number.</p>
</dd>

### -field <b>ReturnCode</b>

<dd>
<p>The return code that the driver returns when the <a href="https://msdn.microsoft.com/bb152e3d-497f-4798-86cc-6f300e24a05c">QueryAuthenticatedChannel(D3D11_1)</a> function is called.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/90b43bc3-6569-4799-8be3-e4e60f59164f">CreateAuthenticatedChannel(D3D11_1)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406399">D3D11_1DDI_AUTHENTICATED_QUERY_INPUT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406450">D3D11_1DDI_OMAC</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/bb152e3d-497f-4798-86cc-6f300e24a05c">QueryAuthenticatedChannel(D3D11_1)</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D11_1DDI_AUTHENTICATED_QUERY_OUTPUT structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
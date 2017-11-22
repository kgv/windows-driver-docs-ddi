---
UID: NF.rxce.RxCeTearDownTransport
title: RxCeTearDownTransport
author: windows-driver-content
description: RxCeTearDownTransport unbinds an RDBSS transport object.
old-location: ifsk\rxceteardowntransport.htm
ms.assetid: 61376532-c78f-4a22-b8b7-ee55ddcb4b57
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: rxce.h
req.include-header: Rxce.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxCeTearDownTransport
req.alt-loc: rxce.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: RxCeTearDownTransport
req.iface: 
req.product: Windows 10 or later.
---

# RxCeTearDownTransport function



## -description
<p><b>RxCeTearDownTransport</b> unbinds an RDBSS transport object.</p>


## -syntax

````
NTSTATUS RxCeTearDownTransport(
  _In_ PRXCE_TRANSPORT pTransport
);
````


## -parameters
<dl>

### -param <i>pTransport</i> [in]

<dd>
<p>A pointer to the RDBSS transport to be torn down.</p>
</dd>
</dl>

## -returns
<p><b>RxCeTearDownTransport</b> returns STATUS_SUCCESS on success or one of the following error codes on failure: </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The <i>pTransport</i> parameter passed to <b>RxCeTearDownAddress</b> or one of the data members associated with this transport was invalid. </p>

<p> </p>

## -remarks
<p>When <b>RxCeTearDownTransport</b> is successful, the data members in the RXCE_TRANSPORT structure pointed to by the <i>pTransport</i> parameter will be properly uninitialized, the RDBSS transport will be released from the specified TDI transport, and allocated memory for name buffers and provider information will be freed.</p>

<p>If a transport that has not been bound to is specified in the <i>pTransport</i> parameter, no error is returned and the operation returns STATUS_SUCCESS. </p>

<p>When <b>RxCeTearDownTransport</b> is successful, the data members in the RXCE_TRANSPORT structure pointed to by the <i>pTransport</i> parameter will be properly uninitialized, the RDBSS transport will be released from the specified TDI transport, and allocated memory for name buffers and provider information will be freed.</p>

<p>If a transport that has not been bound to is specified in the <i>pTransport</i> parameter, no error is returned and the operation returns STATUS_SUCCESS. </p>

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
<dt>Rxce.h (include Rxce.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553434">RxCeBuildTransport</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxCeTearDownTransport function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
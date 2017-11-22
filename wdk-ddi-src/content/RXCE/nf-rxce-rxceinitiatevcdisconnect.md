---
UID: NF.rxce.RxCeInitiateVCDisconnect
title: RxCeInitiateVCDisconnect
author: windows-driver-content
description: RxCeInitiateVCDisconnect initiates a disconnect on the virtual circuit.
old-location: ifsk\rxceinitiatevcdisconnect.htm
ms.assetid: 978ddc02-9ff0-4798-879c-e4bc99081dcb
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
req.alt-api: RxCeInitiateVCDisconnect
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
ms.keywords: RxCeInitiateVCDisconnect
req.iface: 
req.product: Windows 10 or later.
---

# RxCeInitiateVCDisconnect function



## -description
<p><b>RxCeInitiateVCDisconnect</b> initiates a disconnect on the virtual circuit.</p>


## -syntax

````
NTSTATUS RxCeInitiateVCDisconnect(
  _In_ PRXCE_VC pVc
);
````


## -parameters
<dl>

### -param <i>pVc</i> [in]

<dd>
<p>A pointer to the virtual circuit structure to be disconnected. </p>
</dd>
</dl>

## -returns
<p><b>RxCeInitiateVCDisconnect</b> returns STATUS_SUCCESS on success or one of the following error codes on failure: </p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>The allocation of nonpaged pool memory needed by this routine failed. </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The <i>pVc</i> parameter passed to this routine was invalid. </p>

<p> </p>

## -remarks
<p><b>RxCeInitiateVCDisconnect</b> must be called in the context of a system worker thread. </p>

<p><b>RxCeInitiateVCDisconnect</b> must be called in the context of a system worker thread. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553439">RxCeBuildVC</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554332">RxCeTearDownVC</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxCeInitiateVCDisconnect function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
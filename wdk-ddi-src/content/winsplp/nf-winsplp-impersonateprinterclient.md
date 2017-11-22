---
UID: NF.winsplp.ImpersonatePrinterClient
title: ImpersonatePrinterClient
author: windows-driver-content
description: ImpersonatePrinterClient resumes impersonation of the client, completing the operation begun by RevertToPrinterSelf.
old-location: print\impersonateprinterclient.htm
ms.assetid: 8e110b2a-9d13-4e2e-8f27-5a48d838fb3c
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: Winsplp.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ImpersonatePrinterClient
req.alt-loc: Spoolss.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Spoolss.lib
req.dll: Spoolss.dll
req.irql: 
ms.keywords: ImpersonatePrinterClient
req.iface: 
req.product: Windows 10 or later.
---

# ImpersonatePrinterClient function



## -description
<p>ImpersonatePrinterClient resumes impersonation of the client, completing the operation begun by <a href="https://msdn.microsoft.com/library/windows/hardware/ff561987">RevertToPrinterSelf</a>.</p>


## -syntax

````
BOOL ImpersonatePrinterClient(
  _In_ HANDLE hToken
);
````


## -parameters
<dl>

### -param <i>hToken</i> [in]

<dd>
<p>Caller-supplied handle to a thread. This parameter must have been previously returned by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff561987">RevertToPrinterSelf</a>.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the function returns <b>TRUE</b>. Otherwise the function returns <b>FALSE</b>. The caller can obtain an error code by calling GetLastError (described in the Microsoft Windows SDK documentation).</p>

## -remarks
<p>This function must be called after a successful call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff561987">RevertToPrinterSelf</a>. It resumes impersonation of the client and cleans up the thread handle.</p>

<p>This function must be called after a successful call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff561987">RevertToPrinterSelf</a>. It resumes impersonation of the client and cleans up the thread handle.</p>

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
<dt>Winsplp.h (include Winsplp.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Spoolss.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Spoolss.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561987">RevertToPrinterSelf</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20ImpersonatePrinterClient function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
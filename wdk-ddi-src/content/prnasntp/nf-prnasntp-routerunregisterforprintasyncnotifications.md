---
UID: NF.prnasntp.RouterUnregisterForPrintAsyncNotifications
title: RouterUnregisterForPrintAsyncNotifications
author: windows-driver-content
description: The RouterUnregisterForPrintAsyncNotifications function unregisters for receiving asynchronous notifications associated with a printer or print server.
old-location: print\routerunregisterforprintasyncnotifications.htm
ms.assetid: 67909e35-fae2-40b7-b39f-58576e932332
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: prnasntp.h
req.include-header: Prnasntp.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RouterUnregisterForPrintAsyncNotifications
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
ms.keywords: RouterUnregisterForPrintAsyncNotifications
req.iface: 
req.product: Windows 10 or later.
---

# RouterUnregisterForPrintAsyncNotifications function



## -description
<p>The <code>RouterUnregisterForPrintAsyncNotifications</code> function unregisters for receiving asynchronous notifications associated with a printer or print server.</p>


## -syntax

````
HRESULT RouterUnregisterForPrintAsyncNotifications(
  _In_ HANDLE hNotify
);
````


## -parameters
<dl>

### -param <i>hNotify</i> [in]

<dd>
<p>The registration handle returned by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562024">RouterRegisterForPrintAsyncNotifications</a> function.</p>
</dd>
</dl>

## -returns
<p>This function returns S_OK on success, and a standard COM error code otherwise.</p>

## -remarks


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
<dt>Prnasntp.h (include Prnasntp.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562024">RouterRegisterForPrintAsyncNotifications</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20RouterUnregisterForPrintAsyncNotifications function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
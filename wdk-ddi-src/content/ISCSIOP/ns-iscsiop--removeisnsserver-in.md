---
UID: NS.iscsiop._RemoveiSNSServer_IN
title: RemoveiSNSServer_IN
author: windows-driver-content
description: The RemoveiSNSServer_IN structure holds the input data for the user-mode RemoveISNSServer method, which is used to remove an iSNS server entry.
old-location: storage\removeisnsserver_in.htm
ms.assetid: 10e72834-4866-42f2-842e-0a30278acab8
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsiop.h
req.include-header: Iscsiop.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RemoveiSNSServer_IN
req.alt-loc: iscsiop.h
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
ms.keywords: RemoveiSNSServer_IN, RemoveiSNSServer_IN, *PRemoveiSNSServer_IN
req.iface: 
---

# RemoveiSNSServer_IN structure



## -description
<p>The RemoveiSNSServer_IN structure holds the input data for the user-mode <b>RemoveISNSServer</b> method, which is used to remove an iSNS server entry.</p>


## -syntax

````
typedef struct _RemoveiSNSServer_IN {
  WCHAR iSNSServerName[223 + 1];
} RemoveiSNSServer_IN, *PRemoveiSNSServer_IN;
````


## -struct-fields
<dl>

### -field <b>iSNSServerName</b>

<dd>
<p>The name of the iSNS server to remove from the initiator's list.</p>
</dd>
</dl>

## -remarks
<p>It is optional that you implement this method.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Iscsiop.h (include Iscsiop.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563982">RemoveiSNSServer_OUT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20RemoveiSNSServer_IN structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
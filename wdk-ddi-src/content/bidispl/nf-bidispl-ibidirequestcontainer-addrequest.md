---
UID: NF.bidispl.IBidiRequestContainer.AddRequest
title: IBidiRequestContainer::AddRequest
author: windows-driver-content
description: The IBidiRequestContainer::AddRequest method adds a request to the request list.
old-location: print\ibidirequestcontainer_ibidirequestcontainer__addrequest.htm
ms.assetid: 69a97816-2994-4eec-b2ab-a545195e3776
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: bidispl.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Windows XP
req.target-min-winversvr: Windows Server 2003
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IBidiRequestContainer.IBidiRequestContainer::AddRequest
req.alt-loc: bidispl.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: Bidispl.dll
req.irql: PASSIVE_LEVEL
ms.keywords: IBidiRequestContainer, AddRequest, IBidiRequestContainer::AddRequest
req.iface: IBidiRequestContainer
---

# IBidiRequestContainer::AddRequest method



## -description
<p>The <b>IBidiRequestContainer::AddRequest</b> method adds a request to the request list.</p>


## -syntax

````
HRESULT IBidiRequestContainer::AddRequest(
  [in] IBidiRequest *pRequest
);
````


## -parameters
<dl>

### -param <i>pRequest</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/dd144969">IBidiRequest</a> interface.</p>
</dd>
</dl>

## -returns
<p>The method returns one of the following values. For more information about COM error codes, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544310">Error Handling</a>.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The operation was successfully carried out.</p><dl>
<dt><b>E_HANDLE</b></dt>
</dl><p>The interface handle was invalid.</p><dl>
<dt><b>None of the above</b></dt>
</dl><p>The <b>HRESULT</b> contains an error code corresponding to the last error.</p>

<p> </p>

## -remarks
<p>This is similar to adding an item in a link list. In this case, <a href="https://msdn.microsoft.com/library/windows/hardware/dd144970">IBidiRequestContainer</a> will hold a reference to <i>pRequest</i> by calling pRequest-&gt;AddRef.</p>

<p>This is similar to adding an item in a link list. In this case, <a href="https://msdn.microsoft.com/library/windows/hardware/dd144970">IBidiRequestContainer</a> will hold a reference to <i>pRequest</i> by calling pRequest-&gt;AddRef.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows XP</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2003</p>
</td>
</tr>
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
<dt>Bidispl.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Bidispl.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545163">Bidirectional Communication Interfaces</a>
</dt>
<dt>
<a href="NULL">Bidirectional Communication Schema</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dd144969">IBidiRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dd144970">IBidiRequestContainer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IBidiRequestContainer::IBidiRequestContainer::AddRequest method%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
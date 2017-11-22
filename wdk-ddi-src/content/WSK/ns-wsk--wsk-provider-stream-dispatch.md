---
UID: NS.wsk._WSK_PROVIDER_STREAM_DISPATCH
title: WSK_PROVIDER_STREAM_DISPATCH
author: windows-driver-content
description: The WSK_PROVIDER_STREAM_DISPATCH structure specifies the WSK subsystem's table of functions for a stream socket.
old-location: netvista\wsk_provider_stream_dispatch.htm
ms.assetid: A10B901E-9987-40E9-976B-4CD9455E0AEE
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: wsk.h
req.include-header: Wsk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1703
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WSK_PROVIDER_STREAM_DISPATCH
req.alt-loc: wsk.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: WSK_PROVIDER_STREAM_DISPATCH, WSK_PROVIDER_STREAM_DISPATCH, *PWSK_PROVIDER_STREAM_DISPATCH
req.iface: 
req.product: Windows 10 or later.
---

# WSK_PROVIDER_STREAM_DISPATCH structure



## -description
<p>The WSK_PROVIDER_STREAM_DISPATCH structure specifies the WSK subsystem's table of functions for a
  stream socket.
   
  </p>


## -syntax

````
typedef struct _WSK_PROVIDER_STREAM_DISPATCH {
  WSK_PROVIDER_BASIC_DISPATCH      Basic;
  PFN_WSK_BIND                     WskBind;
  PFN_WSK_ACCEPT                   WskAccept;
  PFN_WSK_CONNECT                  WskConnect;
  PFN_WSK_LISTEN                   WskListen;
  PFN_WSK_SEND                     WskSend;
  PFN_WSK_RECEIVE                  WskReceive;
  PFN_WSK_DISCONNECT               WskDisconnect;
  PFN_RELEASE_DATA_INDICATION_LIST WskRelease;
  PFN_WSK_GET_LOCAL_ADDRESS        WskGetLocalAddress;
  PFN_WSK_GET_REMOTE_ADDRESS       WskGetRemoteAddress;
  PFN_WSK_CONNECT_EX               WskConnectEx;
} WSK_PROVIDER_STREAM_DISPATCH, *PWSK_PROVIDER_STREAM_DISPATCH;
````


## -struct-fields
<dl>

### -field <b>Basic</b>

<dd>
<p>The members of the 
     <a href="https://msdn.microsoft.com/15cd5336-fe29-4a59-8071-04c802552a5a">
     WSK_PROVIDER_BASIC_DISPATCH</a> structure are included as members of the WSK_PROVIDER_STREAM_DISPATCH
     structure.</p>
</dd>

### -field <b>WskBind</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571121">WskBind</a> function for the socket.</p>
</dd>

### -field <b>WskAccept</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571109">WskAccept</a> function for the socket.</p>
</dd>

### -field <b>WskConnect</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571125">WskConnect</a> function for the socket.</p>
</dd>

### -field <b>WskListen</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/854C2DA1-1763-4354-8B9D-9AE0C60D8F31">WskListen</a> function for the socket.</p>
</dd>

### -field <b>WskSend</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571146">WskSend</a> function for the socket.</p>
</dd>

### -field <b>WskReceive</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571139">WskReceive</a> function for the socket.</p>
</dd>

### -field <b>WskDisconnect</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571129">WskDisconnect</a> function for the
     socket.</p>
</dd>

### -field <b>WskRelease</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571144">WskRelease</a> function for the socket.</p>
</dd>

### -field <b>WskGetLocalAddress</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571133">WskGetLocalAddress</a> function for the
     socket.</p>
</dd>

### -field <b>WskGetRemoteAddress</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571135">WskGetRemoteAddress</a> function for the
     socket.</p>
</dd>

### -field <b>WskConnectEx</b>

<dd>
<p>A pointer to the WSK subsystem's 
     <a href="https://msdn.microsoft.com/1BC518E9-747C-4406-8A2A-40A3BCB0A3AA">WskConnectEx</a> function for the
     socket.</p>
</dd>
</dl>

## -remarks
<p>The member list of the WSK_PROVIDER_STREAM_DISPATCH structure includes an unnamed 
    <a href="https://msdn.microsoft.com/15cd5336-fe29-4a59-8071-04c802552a5a">
    WSK_PROVIDER_BASIC_DISPATCH</a> structure. The compiler that is included with the WDK supports a
    Microsoft-specific extension to the C language that allows unnamed structures within structure
    declarations. The result is that the structure members of the WSK_PROVIDER_BASIC_DISPATCH structure are
    included in the WSK_PROVIDER_STREAM_DISPATCH structure as if they were native members of the
    WSK_PROVIDER_STREAM_DISPATCH structure.</p>

<p>A WSK application receives a pointer to a WSK_PROVIDER_STREAM_DISPATCH structure when the WSK
    application calls the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff571149">WskSocket</a> function to create a stream socket.
    The pointer is contained in the 
    <b>Dispatch</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff571182">WSK_SOCKET</a> structure that is received from the
    WSK subsystem.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Windows 10, version 1703</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wsk.h (include Wsk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/7E682868-1D39-4677-A4EC-E7C9F841EC82">WSK_CLIENT_STREAM_DISPATCH</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571182">WSK_SOCKET</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/15cd5336-fe29-4a59-8071-04c802552a5a">
    WSK_PROVIDER_BASIC_DISPATCH</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571149">WskSocket</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WSK_PROVIDER_STREAM_DISPATCH structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
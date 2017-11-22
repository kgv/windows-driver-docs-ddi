---
UID: NS.wwan._WWAN_DEVICE_SERVICE_SESSION_WRITE
title: WWAN_DEVICE_SERVICE_SESSION_WRITE
author: windows-driver-content
description: The WWAN_DEVICE_SERVICE_SESSION_WRITE structure represents data associated with a device service session write request.
old-location: netvista\wwan_device_service_session_write.htm
ms.assetid: 8134E635-5FC3-4990-A7CC-E43ECEB1FBB6
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with  Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_DEVICE_SERVICE_SESSION_WRITE
req.alt-loc: wwan.h
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
ms.keywords: WWAN_DEVICE_SERVICE_SESSION_WRITE, WWAN_DEVICE_SERVICE_SESSION_WRITE, *PWWAN_DEVICE_SERVICE_SESSION_WRITE
req.iface: 
req.product: Windows 10 or later.
---

# WWAN_DEVICE_SERVICE_SESSION_WRITE structure



## -description
<p>The WWAN_DEVICE_SERVICE_SESSION_WRITE structure represents data associated with a device service session write request.</p>


## -syntax

````
typedef struct _WWAN_DEVICE_SERVICE_SESSION_WRITE {
  ULONG uSessionID;
  ULONG uDataSize;
} WWAN_DEVICE_SERVICE_SESSION_WRITE, *PWWAN_DEVICE_SERVICE_SESSION_WRITE;
````


## -struct-fields
<dl>

### -field <b>uSessionID</b>

<dd>
<p>The session ID of the device service.</p>
</dd>

### -field <b>uDataSize</b>

<dd>
<p>The size, in bytes, of the device service data that follows the structure instance in memory. This value should not exceed the value of the <b>uMaxSessionDataSize</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh831880">WWAN_SUPPORTED_DEVICE_SERVICES</a> structure.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported starting with  Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wwan.h (include Wwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh831860">NDIS_WWAN_DEVICE_SERVICE_SESSION_WRITE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh831880">WWAN_SUPPORTED_DEVICE_SERVICES</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WWAN_DEVICE_SERVICE_SESSION_WRITE structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
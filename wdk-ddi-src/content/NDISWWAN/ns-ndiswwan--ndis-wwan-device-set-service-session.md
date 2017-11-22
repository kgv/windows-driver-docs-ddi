---
UID: NS.ndiswwan._NDIS_WWAN_DEVICE_SET_SERVICE_SESSION
title: NDIS_WWAN_DEVICE_SET_SERVICE_SESSION
author: windows-driver-content
description: The NDIS_WWAN_SET_DEVICE_SERVICE_SESSION structure represents a session state operation to be performed on a device service.
old-location: netvista\ndis_wwan_set_device_service_session.htm
ms.assetid: D68B2071-D32B-4A6A-ACB8-001865CABD92
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndiswwan.h
req.include-header: Ndiswwan.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with  Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_WWAN_SET_DEVICE_SERVICE_SESSION
req.alt-loc: ndiswwan.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NDIS_WWAN_DEVICE_SET_SERVICE_SESSION, NDIS_WWAN_SET_DEVICE_SERVICE_SESSION, *PNDIS_WWAN_SET_DEVICE_SERVICE_SESSION
req.iface: 
---

# NDIS_WWAN_DEVICE_SET_SERVICE_SESSION structure



## -description
<p>The NDIS_WWAN_SET_DEVICE_SERVICE_SESSION structure represents a session state operation to be performed on a device service.</p>


## -syntax

````
typedef struct _NDIS_WWAN_SET_DEVICE_SERVICE_SESSION {
  NDIS_OBJECT_HEADER          Header;
  WWAN_DEVICE_SERVICE_SESSION Session;
} NDIS_WWAN_SET_DEVICE_SERVICE_SESSION, *PNDIS_WWAN_SET_DEVICE_SERVICE_SESSION;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>The header with type, revision, and size information about the NDIS_WWAN_SET_DEVICE_SERVICE_SESSION
     structure. The MB Service sets the header with the values that are shown in the following table when it
     sends the data structure to the miniport driver for 
     <i>set</i> operations. Miniport drivers must set the header with the same values when they send the data
     structure to the MB service.
     </p>
<table>
<tr>
<th>Header submember</th>
<th>Value</th>
</tr>
<tr>
<td>
<p>Type</p>
</td>
<td>
<p>NDIS_OBJECT_TYPE_DEFAULT</p>
</td>
</tr>
<tr>
<td>
<p>Revision</p>
</td>
<td>
<p>NDIS_WWAN_SET_DEVICE_SERVICE_SESSION_REVISION_1</p>
</td>
</tr>
<tr>
<td>
<p>Size</p>
</td>
<td>
<p>sizeof(NDIS_WWAN_SET_DEVICE_SERVICE_SESSION)</p>
</td>
</tr>
</table>
<p> </p>
<p>For more information about these members, see 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>.</p>
</dd>

### -field <b>Session</b>

<dd>
<p>The requested session state set operation.</p>
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
<dt>Ndiswwan.h (include Ndiswwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh831873">WWAN_DEVICE_SERVICE_SESSION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_WWAN_SET_DEVICE_SERVICE_SESSION structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
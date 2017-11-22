---
UID: NS.bthioctl._BTH_SDP_SERVICE_SEARCH_REQUEST
title: BTH_SDP_SERVICE_SEARCH_REQUEST
author: windows-driver-content
description: The BTH_SDP_SERVICE_SEARCH_REQUEST structure contains information pertinent to an SDP service search.
old-location: bltooth\bth_sdp_service_search_request.htm
ms.assetid: d1ef833e-8350-499c-9a3d-408d900c9245
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthioctl.h
req.include-header: Bthioctl.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BTH_SDP_SERVICE_SEARCH_REQUEST
req.alt-loc: bthioctl.h
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
ms.keywords: BTH_SDP_SERVICE_SEARCH_REQUEST, BTH_SDP_SERVICE_SEARCH_REQUEST, *PBTH_SDP_SERVICE_SEARCH_REQUEST
req.iface: 
---

# BTH_SDP_SERVICE_SEARCH_REQUEST structure



## -description
<p>The BTH_SDP_SERVICE_SEARCH_REQUEST structure contains information pertinent to an SDP service
  search.</p>


## -syntax

````
typedef struct _BTH_SDP_SERVICE_SEARCH_REQUEST {
  HANDLE_SDP   hConnection;
  SdpQueryUuid uuids[MAX_UUIDS_IN_QUERY];
} BTH_SDP_SERVICE_SEARCH_REQUEST, *PBTH_SDP_SERVICE_SEARCH_REQUEST;
````


## -struct-fields
<dl>

### -field <b>hConnection</b>

<dd>
<p>A handle to the remote SDP server that is returned by the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536688">IOCTL_BTH_SDP_CONNECT</a> IOCTL.</p>
</dd>

### -field <b>uuids</b>

<dd>
<p>An array of UUIDs that represent the services for which to query. Each entry can be a 2-byte,
     4-byte, or 16-byte type, and there can be a maximum of 12 entries. The array can be terminated before
     all 12 entries are used if a UUID entry contains all zeros.</p>
</dd>
</dl>

## -remarks
<p>This structure is passed as the input buffer to the 
    <a href="https://msdn.microsoft.com/aea2aff2-5983-4583-9cc8-a45401ecdfb6">
    IOCTL_BTH_SDP_SERVICE_SEARCH</a> IOCTL.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Versions: Supported in Windows Vista, and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Bthioctl.h (include Bthioctl.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536688">IOCTL_BTH_SDP_CONNECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536692">IOCTL_BTH_SDP_SERVICE_SEARCH</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20BTH_SDP_SERVICE_SEARCH_REQUEST structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
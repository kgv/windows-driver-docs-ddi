---
UID: NS.1394._GET_LOCAL_HOST_INFO8
title: GET_LOCAL_HOST_INFO8
author: windows-driver-content
description: The GET_LOCAL_HOST_INFO8 structure contains the data returned by a REQUEST_GET_LOCAL_HOST_INFO request with u.GetLocalHostInformation.nLevel set to GET_HOST_DDI_VERSION.
old-location: ieee\get_local_host_info8.htm
ms.assetid: DA30F8BA-B920-458E-B7C7-8D7B7081507A
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: IEEE
req.header: 1394.h
req.include-header: 1394.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GET_LOCAL_HOST_INFO8
req.alt-loc: 1394.h
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
ms.keywords: GET_LOCAL_HOST_INFO8, GET_LOCAL_HOST_INFO8, *PGET_LOCAL_HOST_INFO8
---

# GET_LOCAL_HOST_INFO8 structure



## -description
<p>The <b>GET_LOCAL_HOST_INFO8</b> structure contains the data returned by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff537644">REQUEST_GET_LOCAL_HOST_INFO</a> request with <b>u.GetLocalHostInformation.nLevel</b> set to GET_HOST_DDI_VERSION.</p>


## -syntax

````
typedef struct _GET_LOCAL_HOST_INFO8 {
  USHORT MajorVersion;
  USHORT MinorVersion;
} GET_LOCAL_HOST_INFO8, *PGET_LOCAL_HOST_INFO8;
````


## -struct-fields
<dl>

### -field <b>MajorVersion</b>

<dd>
<p>The major version of the 1394 bus driver interface.</p>
</dd>

### -field <b>MinorVersion</b>

<dd>
<p>The minor version of the 1394 bus driver interface.</p>
</dd>
</dl>

## -remarks
<p>A client driver can determine whether the 1394 bus driver
loaded in the IEEE 1394 driver stack is the new 1394 bus driver or the legacy
1394 bus driver. A new <b>nLevel</b> value has been added
to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff537644">REQUEST_GET_LOCAL_HOST_INFO</a> I/O
request to return the version of the DDIs that the 1394 bus driver supports.
</p>

<p>To determine whether the 1394 bus driver is the new 1394 bus
driver or the legacy 1394 bus driver,</p>

<p>If the driver stack contains the new 1394 bus
driver, the request returns a status value of STATUS_SUCCESS. Otherwise, the
legacy 1394 bus driver returns a status value of
STATUS_INVALID_PARAMETER.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7 and later versions.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>1394.h (include 1394.h)</dt>
</dl>
</td>
</tr>
</table>
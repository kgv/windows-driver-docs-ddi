---
UID: NF.ucmtypes.UCM_PD_POWER_DATA_OBJECT_GET_TYPE
title: UCM_PD_POWER_DATA_OBJECT_GET_TYPE
author: windows-driver-content
description: Retrieves the type of Power Data Object from the UCM_PD_POWER_DATA_OBJECT structure.
old-location: buses\ucm_pd_power_data_object_get_type.htm
ms.assetid: ACB0AB92-5EC8-4792-AB40-853FC5AAD125
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: usbref
req.header: ucmtypes.h
req.include-header: Ucmcx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 2.15
req.alt-api: UCM_PD_POWER_DATA_OBJECT_GET_TYPE
req.alt-loc: Ucmtypes.h
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
ms.keywords: UCM_PD_POWER_DATA_OBJECT_GET_TYPE
req.iface: 
req.product: Windows 10 or later.
---

# UCM_PD_POWER_DATA_OBJECT_GET_TYPE function



## -description
<p>Retrieves the type of Power Data Object from the <a href="https://msdn.microsoft.com/library/windows/hardware/mt187935">UCM_PD_POWER_DATA_OBJECT</a> structure. </p>


## -syntax

````
FORCEINLINE  UCM_PD_POWER_DATA_OBJECT_GET_TYPE(
  _In_ PUCM_PD_POWER_DATA_OBJECT Pdo
);
````


## -parameters
<dl>

### -param <i>Pdo</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt187935">UCM_PD_POWER_DATA_OBJECT</a> structure that contains the type of Power Data Object.</p>
</dd>
</dl>

## -returns
<p>Returns the <b>Common.Type</b> member of the  <a href="https://msdn.microsoft.com/library/windows/hardware/mt187935">UCM_PD_POWER_DATA_OBJECT</a> structure.</p>

## -remarks
<p>For information about the Power Data Object including the types of object, see Power Delivery specification. The Type member of <a href="https://msdn.microsoft.com/library/windows/hardware/mt187935">UCM_PD_POWER_DATA_OBJECT</a> indicates the type of Power Data Object.</p>

<p>For information about the Power Data Object including the types of object, see Power Delivery specification. The Type member of <a href="https://msdn.microsoft.com/library/windows/hardware/mt187935">UCM_PD_POWER_DATA_OBJECT</a> indicates the type of Power Data Object.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.15</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.15</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ucmtypes.h (include Ucmcx.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt187935">UCM_PD_POWER_DATA_OBJECT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20UCM_PD_POWER_DATA_OBJECT_GET_TYPE function%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
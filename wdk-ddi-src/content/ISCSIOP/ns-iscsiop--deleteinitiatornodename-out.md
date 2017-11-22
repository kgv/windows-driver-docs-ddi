---
UID: NS.iscsiop._DeleteInitiatorNodeName_OUT
title: DeleteInitiatorNodeName_OUT
author: windows-driver-content
description: The DeleteInitiatorNodeName_OUT structure holds the output data for the DeleteInitiatorNodeName method.
old-location: storage\deleteinitiatornodename_out.htm
ms.assetid: 105f6687-ea0f-45e9-be44-eafdd06156eb
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
req.alt-api: DeleteInitiatorNodeName_OUT
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
ms.keywords: DeleteInitiatorNodeName_OUT, DeleteInitiatorNodeName_OUT, *PDeleteInitiatorNodeName_OUT
req.iface: 
---

# DeleteInitiatorNodeName_OUT structure



## -description
<p>The DeleteInitiatorNodeName_OUT structure holds the output data for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552500">DeleteInitiatorNodeName</a> method.</p>


## -syntax

````
typedef struct _DeleteInitiatorNodeName_OUT {
  ULONG Status;
} DeleteInitiatorNodeName_OUT, *PDeleteInitiatorNodeName_OUT;
````


## -struct-fields
<dl>

### -field <b>Status</b>

<dd>
<p>The status of the <b>DeleteInitiatorNodeName</b> operation. For a list of status qualifiers, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff561568">ISCSI_STATUS_QUALIFIERS</a>. </p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552500">DeleteInitiatorNodeName</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552505">DeleteInitiatorNodeName_IN</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561568">ISCSI_STATUS_QUALIFIERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20DeleteInitiatorNodeName_OUT structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
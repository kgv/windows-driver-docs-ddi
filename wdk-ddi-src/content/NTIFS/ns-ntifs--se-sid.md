---
UID: NS.ntifs._SE_SID
title: SE_SID
author: windows-driver-content
description: The SE_SID union holds the maximum-sized valid Security Identifier (SID). The structure occupies 68-bytes and is suitable for stack allocation.
old-location: ifsk\se_sid.htm
ms.assetid: 6950B71D-B396-494E-A23C-EE37B439FD05
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SE_SID
req.alt-loc: ntifs.h
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
ms.keywords: SE_SID, SE_SID, *PSE_SID
req.iface: 
---

# SE_SID structure



## -description
<p>The <b>SE_SID</b> union holds the maximum-sized valid Security Identifier (SID). The structure occupies 68-bytes and is suitable for stack allocation.</p>


## -syntax

````
typedef union _SE_SID {
  SID   Sid;
  UCHAR Buffer[SECURITY_MAX_SID_SIZE];
} SE_SID, *PSE_SID;
````


## -struct-fields
<dl>

### -field <b>Sid</b>

<dd>
<p>A security identifier structure used to uniquely identify users or groups.</p>
</dd>

### -field <b>Buffer</b>

<dd>
<p>Specifies an array of SECURITY_MAX_SID_SIZE for allocating enough memory for the largest possible SID size.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556740">SID</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20SE_SID union%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
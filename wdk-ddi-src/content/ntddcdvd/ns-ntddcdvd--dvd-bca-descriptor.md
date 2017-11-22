---
UID: NS.ntddcdvd._DVD_BCA_DESCRIPTOR
title: DVD_BCA_DESCRIPTOR
author: windows-driver-content
description: The DVD_BCA_DESCRIPTOR structure is used in conjunction with the IOCTL_DVD_READ_STRUCTURE request to retrieve a DVD burst cutting area (BCA) descriptor.
old-location: storage\dvd_bca_descriptor.htm
ms.assetid: a573beb8-7019-4605-ab37-5871f67c585d
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddcdvd.h
req.include-header: Ntddcdvd.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DVD_BCA_DESCRIPTOR
req.alt-loc: ntddcdvd.h
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
ms.keywords: DVD_BCA_DESCRIPTOR, DVD_BCA_DESCRIPTOR, *PDVD_BCA_DESCRIPTOR
req.iface: 
---

# DVD_BCA_DESCRIPTOR structure



## -description
<p>The DVD_BCA_DESCRIPTOR structure is used in conjunction with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560426">IOCTL_DVD_READ_STRUCTURE</a> request to retrieve a DVD burst cutting area (BCA) descriptor. </p>


## -syntax

````
typedef struct _DVD_BCA_DESCRIPTOR {
  UCHAR BCAInformation[];
} DVD_BCA_DESCRIPTOR, *PDVD_BCA_DESCRIPTOR;
````


## -struct-fields
<dl>

### -field <b>BCAInformation</b>

<dd>
<p>Contains an array that holds vendor-defined information retrieved from the burst cutting area.</p>
</dd>
</dl>

## -remarks
<p>The contents of the BCA region are specified by the media manufacturer. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddcdvd.h (include Ntddcdvd.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560426">IOCTL_DVD_READ_STRUCTURE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20DVD_BCA_DESCRIPTOR structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
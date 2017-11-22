---
UID: NS.ntddcdvd._AACS_VOLUME_ID
title: AACS_VOLUME_ID
author: windows-driver-content
description: The AACS_VOLUME_ID structure contains an Advanced Access Content System (AACS) volume ID and the corresponding message authentication code (MAC).
old-location: storage\aacs_volume_id.htm
ms.assetid: 3ad7a253-cc55-4613-8086-b8d08d9bd54f
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
req.alt-api: AACS_VOLUME_ID
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
ms.keywords: AACS_VOLUME_ID, AACS_VOLUME_ID, *PAACS_VOLUME_ID
req.iface: 
---

# AACS_VOLUME_ID structure



## -description
<p>The AACS_VOLUME_ID structure contains an Advanced Access Content System (AACS) volume ID and the corresponding message authentication code (MAC).</p>


## -syntax

````
typedef struct _AACS_VOLUME_ID {
  UCHAR VolumeID[16];
  UCHAR MAC[16];
} AACS_VOLUME_ID, *PAACS_VOLUME_ID;
````


## -struct-fields
<dl>

### -field <b>VolumeID</b>

<dd>
<p>The volume identifier.</p>
</dd>

### -field <b>MAC</b>

<dd>
<p>The message authentication code (MAC) that the client uses to verify that the volume identifier is for the current AACS authentication sequence.</p>
</dd>
</dl>

## -remarks
<p>Clients retrieve an AACS volume ID with an <a href="https://msdn.microsoft.com/library/windows/hardware/ff559293">IOCTL_AACS_READ_VOLUME_ID</a> request.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559293">IOCTL_AACS_READ_VOLUME_ID</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20AACS_VOLUME_ID structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NS.ntddcdrm._CDROM_AUDIO_CONTROL
title: CDROM_AUDIO_CONTROL
author: windows-driver-content
description: The CDROM_AUDIO_CONTROL structure is used in conjunction with the IOCTL_CDROM_GET_CONTROL request to report the audio playback mode.
old-location: storage\cdrom_audio_control.htm
ms.assetid: f99ad24d-e1cf-4381-93b9-c10e4b19b401
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddcdrm.h
req.include-header: Ntddcdrm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CDROM_AUDIO_CONTROL
req.alt-loc: ntddcdrm.h
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
ms.keywords: CDROM_AUDIO_CONTROL, CDROM_AUDIO_CONTROL, *PCDROM_AUDIO_CONTROL
req.iface: 
---

# CDROM_AUDIO_CONTROL structure



## -description
<p>The CDROM_AUDIO_CONTROL structure is used in conjunction with the IOCTL_CDROM_GET_CONTROL request to report the audio playback mode. </p>


## -syntax

````
typedef struct _CDROM_AUDIO_CONTROL {
  UCHAR  LbaFormat;
  USHORT LogicalBlocksPerSecond;
} CDROM_AUDIO_CONTROL, *PCDROM_AUDIO_CONTROL;
````


## -struct-fields
<dl>

### -field <b>LbaFormat</b>

<dd>
<p>Contains the logical block address (LBA) format.  </p>
</dd>

### -field <b>LogicalBlocksPerSecond</b>

<dd>
<p>Contains the number of logical blocks per second.</p>
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
<dt>Ntddcdrm.h (include Ntddcdrm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559336">IOCTL_CDROM_GET_CONTROL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20CDROM_AUDIO_CONTROL structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NS.hbaapi.HBA_FcpScsiEntryV2
title: HBA_FcpScsiEntryV2
author: windows-driver-content
description: The HBA_FcpScsiEntryV2 structure defines a mapping between an operating system identifier for a logical unit and the corresponding fibre channel protocol (FCP) identifier for the logical unit.
old-location: storage\hba_fcpscsientryv2.htm
ms.assetid: 28f0118b-8c16-4075-8dc9-78e1e2636f02
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: hbaapi.h
req.include-header: Hbaapi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HBA_FCPSCSIENTRYV2
req.alt-loc: hbaapi.h
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
ms.keywords: HBA_FcpScsiEntryV2, HBA_FCPSCSIENTRYV2, *PHBA_FCPSCSIENTRYV2
req.iface: 
---

# HBA_FcpScsiEntryV2 structure



## -description
<p>The HBA_FcpScsiEntryV2 structure defines a mapping between an operating system identifier for a logical unit and the corresponding fibre channel protocol (FCP) identifier for the logical unit. </p>


## -syntax

````
typedef struct HBA_FcpScsiEntryV2 {
  HBA_SCSIID ScsiId;
  HBA_FCPID  FcpId;
  HBA_LUID   LUID;
} HBA_FCPSCSIENTRYV2, *PHBA_FCPSCSIENTRYV2;
````


## -struct-fields
<dl>

### -field <b>ScsiId</b>

<dd>
<p>Contains a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff557191">HBA_ScsiId</a> that holds information that the operating system uses to identify a SCSI device. </p>
</dd>

### -field <b>FcpId</b>

<dd>
<p>Contains a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff556062">HBA_FcpId</a> that uniquely identifies the device anywhere on the fibre channel network. </p>
</dd>

### -field <b>LUID</b>

<dd>
<p>Contains a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff557091">HBA_LUID</a> that holds a logical unit descriptor for the device that the operating system derives from SCSI inquiry data. </p>
</dd>
</dl>

## -remarks
<p>The HBA_FcpScsiEntryV2 structure includes all of the information contained in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556064">HBA_FcpScsiEntry</a> structure and, in addition, contains the identification descriptor for the logical unit derived from SCSI inquiry data.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hbaapi.h (include Hbaapi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556062">HBA_FcpId</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556064">HBA_FcpScsiEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557091">HBA_LUID</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557191">HBA_ScsiId</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20HBA_FcpScsiEntryV2 structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
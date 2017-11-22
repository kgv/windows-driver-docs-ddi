---
UID: NS.ntdddisk._SET_PARTITION_INFORMATION_EX
title: SET_PARTITION_INFORMATION_EX
author: windows-driver-content
description: SET_PARTITION_INFORMATION_EX is used with the IOCTL IOCTL_DISK_SET_PARTITION_INFO_EX to set information for a specific partition.
old-location: storage\set_partition_information_ex.htm
ms.assetid: a30c10d4-5e85-4a59-b262-054a6fdc2fb8
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntdddisk.h
req.include-header: Ntdddisk.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SET_PARTITION_INFORMATION_EX
req.alt-loc: ntdddisk.h
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
ms.keywords: SET_PARTITION_INFORMATION_EX, SET_PARTITION_INFORMATION_EX, *PSET_PARTITION_INFORMATION_EX
req.iface: 
---

# SET_PARTITION_INFORMATION_EX structure



## -description
<p><b>SET_PARTITION_INFORMATION_EX</b> is used with the IOCTL <a href="https://msdn.microsoft.com/library/windows/hardware/ff560417">IOCTL_DISK_SET_PARTITION_INFO_EX</a> to set information for a specific partition.</p>


## -syntax

````
typedef struct _SET_PARTITION_INFORMATION_EX {
  PARTITION_STYLE PartitionStyle;
  union {
    SET_PARTITION_INFORMATION_MBR Mbr;
    SET_PARTITION_INFORMATION_GPT Gpt;
  };
} SET_PARTITION_INFORMATION_EX, *PSET_PARTITION_INFORMATION_EX;
````


## -struct-fields
<dl>

### -field <b>PartitionStyle</b>

<dd>
<p>Takes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563773">PARTITION_STYLE</a> enumerated value that specifies the type of partition table that contains the partition.</p>
</dd>

### -field <b>Mbr</b>

<dd>
<p>Contains the information for a Master Boot Record partition that is not held in common with a GUID Partition Table partition. This member is valid when <b>PartitionStyle</b> member is set to PARTITION_STYLE_MBR. For a definition of this structure, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff566198">SET_PARTITION_INFORMATION_MBR</a>.</p>
</dd>

### -field <b>Gpt</b>

<dd>
<p>Contains the information for a GUID Partition Table partition that is not held in common with a Master Boot Record partition. This member is valid when <b>PartitionStyle</b> member is set to PARTITION_STYLE_GPT. For a definition of this structure, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff566196">SET_PARTITION_INFORMATION_GPT</a>.</p>
</dd>
</dl>

## -remarks
<p>In the case of GPT partitions, any value that can be retrieved from the partition can also be set. In the MBR case, only the partition signature can be set.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntdddisk.h (include Ntdddisk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566198">SET_PARTITION_INFORMATION_MBR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566196">SET_PARTITION_INFORMATION_GPT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560417">IOCTL_DISK_SET_PARTITION_INFO_EX</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20SET_PARTITION_INFORMATION_EX structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
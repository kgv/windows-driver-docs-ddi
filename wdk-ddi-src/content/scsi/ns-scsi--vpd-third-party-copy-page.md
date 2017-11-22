---
UID: NS.scsi._VPD_THIRD_PARTY_COPY_PAGE
title: VPD_THIRD_PARTY_COPY_PAGE
author: windows-driver-content
description: The VPD_THIRD_PARTY_COPY_PAGE structure defines the vital product data (VPD) page for offload data transfer operations.
old-location: storage\vpd_third_party_copy_page.htm
ms.assetid: E8D9E05C-26C3-474C-854F-9AD12C8834DF
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: scsi.h
req.include-header: Scsi.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: VPD_THIRD_PARTY_COPY_PAGE
req.alt-loc: scsi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: VPD_THIRD_PARTY_COPY_PAGE, VPD_THIRD_PARTY_COPY_PAGE, *PVPD_THIRD_PARTY_COPY_PAGE
req.iface: 
req.product: Windows 10 or later.
---

# VPD_THIRD_PARTY_COPY_PAGE structure



## -description
<p>The <b>VPD_THIRD_PARTY_COPY_PAGE</b> structure defines the vital product data (VPD) page for offload data transfer operations.</p>


## -syntax

````
typedef struct _VPD_THIRD_PARTY_COPY_PAGE {
  UCHAR DeviceType  :5;
  UCHAR DeviceTypeQualifier  :3;
  UCHAR PageCode;
  UCHAR PageLength[2];
  UCHAR ThirdPartyCopyDescriptors[ANYSIZE_ARRAY];
} VPD_THIRD_PARTY_COPY_PAGE, *PVPD_THIRD_PARTY_COPY_PAGE;
````


## -struct-fields
<dl>

### -field <b>DeviceType</b>

<dd>
<p>The device type. This is the same device type defined for use in the inquiry data for the storage device.</p>
</dd>

### -field <b>DeviceTypeQualifier</b>

<dd>
<p>A qualifier code for the device. Currently, <b>DEVICE_CONNECTED</b>, is the only valid value.</p>
</dd>

### -field <b>PageCode</b>

<dd>
<p>The page code for the VPD third party copy page. This page code is defined as 0x8f.</p>
</dd>

### -field <b>PageLength</b>

<dd>
<p>The length, in bytes, of the VPD page. For offload data transfer on Windows, <b>PageLength</b> must be &gt;= 0x24.</p>
</dd>

### -field <b>ThirdPartyCopyDescriptors</b>

<dd>
<p>Support descriptors for copy operations. On Windows systems, <b>ThirdPartyCopyDescriptors</b>  will contain one descriptor formatted as a <a href="https://msdn.microsoft.com/library/windows/hardware/hh967745">WINDOWS_BLOCK_DEVICE_TOKEN_LIMITS_DESCRIPTOR</a> structure.</p>
</dd>
</dl>

## -remarks
<p>All multibyte values are in big endian format. Prior to evaluation, these values must be converted to match the endian format of the current platform.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Scsi.h (include Scsi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967745">WINDOWS_BLOCK_DEVICE_TOKEN_LIMITS_DESCRIPTOR</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20VPD_THIRD_PARTY_COPY_PAGE structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
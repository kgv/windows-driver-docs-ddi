---
UID: NS.scsi._SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR
title: SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR
author: windows-driver-content
description: The SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR structure specifies the status and additional status of a download microcode.
old-location: storage\ses_download_microcode_status_descriptor.htm
ms.assetid: af686e7a-9426-4151-8ac4-d95ae1689b4c
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: scsi.h
req.include-header: Minitape.h, Storport.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 10, version 1709 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR
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
ms.keywords: SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR, SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR, *PSES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR
req.iface: 
req.product: Windows 10 or later.
---

# SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR structure



## -description
<p>The <b>SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR</b> structure specifies the status and additional status of a download microcode.</p>


## -syntax

````
typedef struct _SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR {
  UCHAR  Reserved1;
  UCHAR  SubEnclosureId;
  UCHAR  Status;
  UCHAR  AdditionalStatus;
  UCHAR  MaximumImageSize[4];
  UCHAR  Reserved2[3];
  UCHAR  ExpectedBufferId;
  UCHAR  ExpectedBufferOffset;
} SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR, *PSES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR;
````


## -struct-fields
<dl>

### -field <b>Reserved1</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>SubEnclosureId</b>

<dd>
<p>Specifies the subenclosure to which the download microcode
status descriptor applies to.</p>
</dd>

### -field <b>Status</b>

<dd>
<p> Specifies the status of download microcode
operations for the subenclosure. After reporting a code indicating completion, the
enclosure services process shall set this field to 0x00 and shall
set the <i>AdditionalStatus</i> field to 0x00. Status may can contain one of the following values:</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x00

</dl>
</td>
<td width="60%">
<p>No download microcode operation is in progress.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x01

</dl>
</td>
<td width="60%">
<p>Download microcode operation is in progress. The enclosure services process has
received one or more Download Microcode Control diagnostic pages and is awaiting
additional microcode data.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x02

</dl>
</td>
<td width="60%">
<p>Download microcode operation data transfer is complete, currently updating nonvolatile
storage.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x03

</dl>
</td>
<td width="60%">
<p>The enclosure services process is currently updating nonvolatile storage with deferred
microcode.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x04 to 0x0F

</dl>
</td>
<td width="60%">
<p>Reserved for codes indicating interim status</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x10

</dl>
</td>
<td width="60%">
<p>Download microcode operation complete with no error. The enclosure services process
begins using the new microcode after returning this status.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x11

</dl>
</td>
<td width="60%">
<p>Download microcode operation complete with no error. The enclosure services process
(e.g., a standalone enclosure services process) begins using the new microcode after the
next hard reset or power on.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x12

</dl>
</td>
<td width="60%">
<p>Download microcode operation complete with no error. The enclosure services process
(e.g., an attached enclosure services process) begins using the new microcode after the
next power on.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x13

</dl>
</td>
<td width="60%">
<p>Download microcode operation complete with no error. The enclosure services process
(e.g., an attached enclosure services process) begins using the new microcode after either processing a <a href="storage._ses_download_microcode_control_diagnostic_page">SES_DOWNLOAD_MICROCODE_CONTROL_DIAGNOSTIC_PAGE</a> specifying the activate deferred microcode mode, hard reset, or power on.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x14 to 0x6F

</dl>
</td>
<td width="60%">
<p>Reserved for codes indicating no error.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x70 to 0x7F

</dl>
</td>
<td width="60%">
<p>Vendor specific</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x80

</dl>
</td>
<td width="60%">
<p>Error in one or more of the Download Microcode Control diagnostic page fields. </p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x81

</dl>
</td>
<td width="60%">
<p>Specifies a Microcode image error.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x82

</dl>
</td>
<td width="60%">
<p>Download microcode timeout. The enclosure services process
may discard microcode data after a vendor specific amount of time, if it does not receive
the entire microcode image.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x83

</dl>
</td>
<td width="60%">
<p>Internal error in the download microcode operation. New microcode image is needed
before a hard reset or power on</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x84

</dl>
</td>
<td width="60%">
<p>Internal error in the download microcode operation. Hard reset and power on safe</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x00

</dl>
</td>
<td width="60%">
<p>Processed a <a href="storage._ses_download_microcode_control_diagnostic_page">SES_DOWNLOAD_MICROCODE_CONTROL_DIAGNOSTIC_PAGE</a> with the <i>Mode</i> field set to 0x0F (i.e., activate deferred microcode), if there is no deferred microcode.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0x86 to 0x0EF

</dl>
</td>
<td width="60%">
<p>Reserved for codes indicating errors.</p>
</td>
</tr>
<tr>
<td width="40%">
<dl>

### -field 0xF0 to 0xFF

</dl>
</td>
<td width="60%">
<p>Vendor Specific</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>AdditionalStatus</b>

<dd>
<p>Provides an additional status value for certain
values of <i>Status</i> .</p>
</dd>

### -field <b>MaximumImageSize</b>

<dd>
<p>Indicates the maximum size in bytes of the
microcode image that the enclosure services process accepts. The image may be delivered using one or
more <a href="storage._ses_download_microcode_control_diagnostic_page">SES_DOWNLOAD_MICROCODE_CONTROL_DIAGNOSTIC_PAGE</a>.</p>
</dd>

### -field <b>Reserved2</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>ExpectedBufferId</b>

<dd>
<p>Indicates the next value that the
enclosure services process expects in the <i>BufferId</i> field in <a href="storage._ses_download_microcode_control_diagnostic_page">SES_DOWNLOAD_MICROCODE_CONTROL_DIAGNOSTIC_PAGE</a>.</p>
</dd>

### -field <b>ExpectedBufferOffset</b>

<dd>
<p>Indicates the next value that the
enclosure services process expects in the <i>BufferOffset</i> field in <a href="storage._ses_download_microcode_control_diagnostic_page">SES_DOWNLOAD_MICROCODE_CONTROL_DIAGNOSTIC_PAGE</a>. If the enclosure services process accepts arbitrary <i>BufferOffset</i> values, then it shall set <i>ExpectedBufferOffset</i> to 0xFFFFFFFF.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 10, version 1709 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Scsi.h (include Minitape.h or Storport.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage._ses_download_microcode_control_diagnostic_page">SES_DOWNLOAD_MICROCODE_CONTROL_DIAGNOSTIC_PAGE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20SES_DOWNLOAD_MICROCODE_STATUS_DESCRIPTOR structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NS.ntddk._WHEA_TIMESTAMP
title: WHEA_TIMESTAMP
author: windows-driver-content
description: The WHEA_TIMESTAMP union describes the time that an error was reported to the operating system.
old-location: whea\whea_timestamp.htm
ms.assetid: 70a6555d-1da9-4013-911a-4a9d011b0205
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: whea
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Windows
req.target-min-winverclnt: Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WHEA_TIMESTAMP
req.alt-loc: ntddk.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WHEA_TIMESTAMP, WHEA_TIMESTAMP, *PWHEA_TIMESTAMP
req.iface: 
---

# WHEA_TIMESTAMP structure



## -description
<p>The WHEA_TIMESTAMP union describes the time that an error was reported to the operating system.</p>


## -syntax

````
typedef union _WHEA_TIMESTAMP {
  struct {
    ULONGLONG Seconds  :8;
    ULONGLONG Minutes  :8;
    ULONGLONG Hours  :8;
    ULONGLONG Precise  :1;
    ULONGLONG Reserved  :7;
    ULONGLONG Day  :8;
    ULONGLONG Month  :8;
    ULONGLONG Year  :8;
    ULONGLONG Century  :8;
  };
  LARGE_INTEGER AsLARGE_INTEGER;
} WHEA_TIMESTAMP, *PWHEA_TIMESTAMP;
````


## -struct-fields
<dl>

### -field <b>Seconds</b>

<dd>
<p>The number of seconds past the minute.</p>
</dd>

### -field <b>Minutes</b>

<dd>
<p>The number of minutes past the hour.</p>
</dd>

### -field <b>Hours</b>

<dd>
<p>The hour in the day.</p>
</dd>

### -field <b>Precise</b>

<dd>
<p>If this member is set to 1, the timestamp correlates precisely to the time of the error event.</p>
<div class="alert"><b>Note</b>  This member is supported in Windows 7 and later versions of Windows.</div>
<div> </div>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>Day</b>

<dd>
<p>The day of the month.</p>
</dd>

### -field <b>Month</b>

<dd>
<p>The month of the year.</p>
</dd>

### -field <b>Year</b>

<dd>
<p>The year within the century.</p>
</dd>

### -field <b>Century</b>

<dd>
<p>The century.</p>
</dd>

### -field <b>AsLARGE_INTEGER</b>

<dd>
<p>A LARGE_INTEGER representation of the contents of the WHEA_TIMESTAMP union.</p>
</dd>
</dl>

## -remarks
<p>A WHEA_TIMESTAMP union is contained within the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560487">WHEA_ERROR_RECORD_HEADER</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560487">WHEA_ERROR_RECORD_HEADER</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [whea\whea]:%20WHEA_TIMESTAMP union%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
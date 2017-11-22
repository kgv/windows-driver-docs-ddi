---
UID: NS.wdm._COUNTED_REASON_CONTEXT
title: COUNTED_REASON_CONTEXT
author: windows-driver-content
description: The COUNTED_REASON_CONTEXT structure contains one or more strings that give reasons for a power request.
old-location: kernel\counted_reason_context.htm
ms.assetid: beb17d50-d99a-4baf-99bd-9f42fbea0478
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Supported in Windows 7 and later versions of the Windows operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: COUNTED_REASON_CONTEXT
req.alt-loc: wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
ms.keywords: COUNTED_REASON_CONTEXT, COUNTED_REASON_CONTEXT, *PCOUNTED_REASON_CONTEXT
req.iface: 
req.product: Windows 10 or later.
---

# COUNTED_REASON_CONTEXT structure



## -description
<p>The <b>COUNTED_REASON_CONTEXT</b> structure contains one or more strings that give reasons for a power request.</p>


## -syntax

````
typedef struct _COUNTED_REASON_CONTEXT {
  ULONG Version;
  ULONG Flags;
  union {
    struct {
      UNICODE_STRING  ResourceFileName;
      USHORT          ResourceReasonId;
      ULONG           StringCount;
      PUNICODE_STRING ReasonStrings;
    };
    UNICODE_STRING SimpleString;
  };
} COUNTED_REASON_CONTEXT, *PCOUNTED_REASON_CONTEXT;
````


## -struct-fields
<dl>

### -field <b>Version</b>

<dd>
<p>The version number of the structure. Set this member to DIAGNOSTIC_REASON_VERSION.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Indicates whether the structure contains a simple reason string or a detailed set of reason strings. Set this member to one of the following constants:</p>
<ul>
<li>
<p>DIAGNOSTIC_REASON_SIMPLE_STRING</p>
</li>
<li>
<p>DIAGNOSTIC_REASON_DETAILED_STRING</p>
</li>
</ul>
<p>If <b>Flags</b> = DIAGNOSTIC_REASON_SIMPLE_STRING, the <b>SimpleString</b> member of the union is valid. If <b>Flags</b> = DIAGNOSTIC_REASON_DETAILED_STRING, the <b>ResourceFileName</b>, <b>ResourceReasonId</b>, <b>StringCount</b>, and <b>ReasonStrings</b> members are valid (and the <b>SimpleString</b> member is not valid).</p>
</dd>

### -field <b>ResourceFileName</b>

<dd>
<p>A pointer to a wide-character, null-terminated string that contains the pathname of a resource file. This resource file contains one or more localized strings that give reasons for a power request. This member is optional and can be specified as <b>NULL</b> or as an empty string if no resource file is required. This member is valid only if <b>Flags</b> = DIAGNOSTIC_REASON_DETAILED_STRING. </p>
</dd>

### -field <b>ResourceReasonId</b>

<dd>
<p>The resource ID assigned to the first reason string in the resource file that is specified by <b>ResourceFileName</b>. This member is valid only if <b>Flags</b> = DIAGNOSTIC_REASON_DETAILED_STRING. </p>
</dd>

### -field <b>StringCount</b>

<dd>
<p>The number of reason strings in the <b>ReasonStrings</b> array or in the resource file that is specified by <b>ResourceFileName</b>. This member is valid only if <b>Flags</b> = DIAGNOSTIC_REASON_DETAILED_STRING. </p>
</dd>

### -field <b>ReasonStrings</b>

<dd>
<p>A pointer to an array of string pointers. Each array element is a pointer to a wide-character, null-terminated string. The number of array elements is specified by <b>StringCount</b>. This member is valid only if <b>Flags</b> = DIAGNOSTIC_REASON_DETAILED_STRING. </p>
</dd>

### -field <b>SimpleString</b>

<dd>
<p>A pointer to a wide-character, null-terminated string that explains the reason for a power request. This member is valid only if <b>Flags</b> = DIAGNOSTIC_REASON_SIMPLE_STRING. </p>
</dd>
</dl>

## -remarks
<p>This structure is used by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559663">PoCreatePowerRequest</a> routine.</p>

<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/ff559829">power manager</a> uses the reason string or strings contained in this structure as a diagnostic aid during functional and performance testing.</p>

<p>The <b>COUNTED_REASON_CONTEXT</b> structure can contain either a simple reason string or a set of detailed reason strings. If <b>Flags</b> = DIAGNOSTIC_REASON_SIMPLE_STRING, the <b>SimpleString</b> member points to a string that explains the reason for the power request. If <b>Flags</b> = DIAGNOSTIC_REASON_DETAILED_STRING, the <b>ResourceFileName</b>, <b>ResourceReasonId</b>, <b>StringCount</b>, and <b>ReasonStrings</b> members can give a detailed set of reasons for the power request.</p>

<p>The DIAGNOSTIC_REASON_DETAILED_STRING flag supports localization. If the localized resource file specified by <b>ResourceFileName</b> exists, the power manager retrieves a set of resource strings from the file and uses these strings in place of the strings contained in the <b>ReasonStrings</b> array. <b>ResourceId</b> specifies the resource index of the first string in the file to use as a reason string, and <b>StringCount</b> specifies the number of resource strings to use as reason strings. The resource strings must have consecutive resource indexes.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in Windows 7 and later versions of the Windows operating system.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559663">PoCreatePowerRequest</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20COUNTED_REASON_CONTEXT structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
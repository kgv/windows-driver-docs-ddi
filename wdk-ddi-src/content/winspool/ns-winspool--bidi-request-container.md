---
UID: NS.winspool._BIDI_REQUEST_CONTAINER
title: BIDI_REQUEST_CONTAINER
author: windows-driver-content
description: The BIDI_REQUEST_CONTAINER structure is a container for a list of bidi requests.
old-location: print\bidi_request_container.htm
ms.assetid: 9892cf0e-23ee-496f-9078-4a2a1fdb19d9
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: winspool.h
req.include-header: Winspool.h
req.target-type: Windows
req.target-min-winverclnt: This structure is available in Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BIDI_REQUEST_CONTAINER
req.alt-loc: winspool.h
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
ms.keywords: BIDI_REQUEST_CONTAINER, BIDI_REQUEST_CONTAINER, *PBIDI_REQUEST_CONTAINER, *LPBIDI_REQUEST_CONTAINER
req.iface: 
req.product: Windows 10 or later.
---

# BIDI_REQUEST_CONTAINER structure



## -description
<p>The BIDI_REQUEST_CONTAINER structure is a container for a list of bidi requests.</p>


## -syntax

````
typedef struct _BIDI_REQUEST_CONTAINER {
  DWORD             Version;
  DWORD             Flags;
  DWORD             Count;
  BIDI_REQUEST_DATA aData[1];
} BIDI_REQUEST_CONTAINER, *PBIDI_REQUEST_CONTAINER, *LPBIDI_REQUEST_CONTAINER;
````


## -struct-fields
<dl>

### -field <b>Version</b>

<dd>
<p>Specifies the version of the bidi API Schema, which is currently 1.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Is a set of flags reserved for system use. This must be zero.</p>
</dd>

### -field <b>Count</b>

<dd>
<p>Specifies the number of bidi requests in the <b>aData</b> member. A container can contain zero or more requests, although a value of zero is valid only if the action is BIDI_ACTION_ENUM_SCHEMA.</p>
</dd>

### -field <b>aData</b>

<dd>
<p>Is an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff545196">BIDI_REQUEST_DATA</a> structures, each holding a single bidi request. </p>
</dd>
</dl>

## -remarks
<p>Even though the <b>aData</b> member of this structure is an array with only a single array element, <b>aData</b>[0] should be thought of as the first element of an array of (possibly) an arbitrarily large size. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>This structure is available in Windows XP and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Winspool.h (include Winspool.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545196">BIDI_REQUEST_DATA</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20BIDI_REQUEST_CONTAINER structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
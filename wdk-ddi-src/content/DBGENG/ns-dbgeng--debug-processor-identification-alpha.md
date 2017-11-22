---
UID: NS.dbgeng._DEBUG_PROCESSOR_IDENTIFICATION_ALPHA
title: DEBUG_PROCESSOR_IDENTIFICATION_ALPHA
author: windows-driver-content
description: Identifies an Alpha processor.
old-location: debugger\debug_processor_identification_alpha.htm
ms.assetid: AE0DB2CC-6364-4B50-8CD3-8EF8B495FBED
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: DbgEng.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DEBUG_PROCESSOR_IDENTIFICATION_ALPHA
req.alt-loc: DbgEng.h
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
ms.keywords: DEBUG_PROCESSOR_IDENTIFICATION_ALPHA, DEBUG_PROCESSOR_IDENTIFICATION_ALPHA, *PDEBUG_PROCESSOR_IDENTIFICATION_ALPHA
req.iface: IDebugSystemObjects4
---

# DEBUG_PROCESSOR_IDENTIFICATION_ALPHA structure



## -description
<p>Identifies an Alpha processor.</p>


## -syntax

````
typedef struct _DEBUG_PROCESSOR_IDENTIFICATION_ALPHA {
  ULONG Type;
  ULONG Revision;
} DEBUG_PROCESSOR_IDENTIFICATION_ALPHA, *PDEBUG_PROCESSOR_IDENTIFICATION_ALPHA;
````


## -struct-fields
<dl>

### -field <b>Type</b>

<dd>
<p>The type of the processor.</p>
</dd>

### -field <b>Revision</b>

<dd>
<p>The revision of the processor.</p>
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
<dt>DbgEng.h (include DbgEng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/2C4C03BC-0D84-4151-B1A1-FE76F0355CD6">DEBUG_PROCESSOR_IDENTIFICATION_ALL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20DEBUG_PROCESSOR_IDENTIFICATION_ALPHA structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
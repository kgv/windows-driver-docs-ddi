---
UID: NF.wdbgexts.ReloadSymbols
title: ReloadSymbols
author: windows-driver-content
description: The ReloadSymbols function deletes symbol information from the debugger so that it can be reloaded as needed. This function behaves the same way as the debugger command .reload.
old-location: debugger\reloadsymbols.htm
ms.assetid: 5778f57c-52dd-43f4-b0f7-d07e0c40512b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: wdbgexts.h
req.include-header: Wdbgexts.h, Wdbgexts.h, Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ReloadSymbols
req.alt-loc: wdbgexts.h
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
ms.keywords: ReloadSymbols
req.iface: 
req.product: Windows 10 or later.
---

# ReloadSymbols function



## -description
<p>The <b>ReloadSymbols</b> function deletes symbol information from the debugger so that it can be reloaded as needed.  This function behaves the same way as the debugger command <a href="https://msdn.microsoft.com/750eb1a2-7af9-4f2d-81ca-9ea0fb157961">.reload</a>.</p>


## -syntax

````
__inline VOID ReloadSymbols(
  _In_opt_ PSTR Arg
);
````


## -parameters
<dl>

### -param <i>Arg</i> [in, optional]

<dd>
<p>Specifies the arguments for the debugger command <b>.reload</b>.  For example, setting <i>Arg</i> to <b>/u ntdll.dll</b> has the same effect as the command <b>.reload /u ntdll.dll</b>.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdbgexts.h (include Wdbgexts.h, Wdbgexts.h, or Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564805">.reload (Reload Module)</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20ReloadSymbols function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
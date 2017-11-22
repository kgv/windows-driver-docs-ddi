---
UID: NF.dbgeng.IDebugSymbols3.GetImagePathWide
title: IDebugSymbols3::GetImagePathWide
author: windows-driver-content
description: The GetImagePathWide method returns the executable image path.
old-location: debugger\getimagepathwide.htm
ms.assetid: 884a5577-3ae8-4444-bf09-3fe4f72dc7d9
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugSymbols3.GetImagePathWide
req.alt-loc: dbgeng.h
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
ms.keywords: IDebugSymbols3, GetImagePathWide, IDebugSymbols3::GetImagePathWide
req.iface: IDebugSymbols3
---

# IDebugSymbols3::GetImagePathWide method



## -description
<p>The <b>GetImagePathWide</b>  method returns the executable image path.</p>


## -syntax

````
HRESULT GetImagePathWide(
  [out, optional] PWSTR  Buffer,
  [in]            ULONG  BufferSize,
  [out, optional] PULONG PathSize
);
````


## -parameters
<dl>

### -param <i>Buffer</i> [out, optional]

<dd>
<p>Receives the executable image path.  This is a string that contains directories separated by semicolons (<b>;</b>).  If <i>Buffer</i> is <b>NULL</b>, this information is not returned.</p>
</dd>

### -param <i>BufferSize</i> [in]

<dd>
<p>Specifies the size, in characters, of the <i>Buffer</i> buffer.</p>
</dd>

### -param <i>PathSize</i> [out, optional]

<dd>
<p>Receives the size, in characters, of the executable image path.</p>
</dd>
</dl>

## -returns
<p>This method may also return other error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>S_FALSE</b></dt>
</dl><p>The method was successful. However, the buffer was not large enough to hold the executable image path and the path was truncated.</p>

<p> </p>

## -remarks
<p>The executable image path is used by the engine when searching for executable images.</p>

<p>The executable image path can consist of several directories separated by semicolons.  These directories are searched in order.</p>

<p>The executable image path is used by the engine when searching for executable images.</p>

<p>The executable image path can consist of several directories separated by semicolons.  These directories are searched in order.</p>

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
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550870">IDebugSymbols3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556708">SetImagePath</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538092">AppendImagePath</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugSymbols3::GetImagePathWide method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
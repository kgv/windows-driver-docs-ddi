---
UID: NF.dbgeng.IDebugControl3.GetPromptText
title: IDebugControl3::GetPromptText
author: windows-driver-content
description: The GetPromptText method returns the standard prompt text that will be prepended to the formatted output specified in the OutputPrompt and OutputPromptVaList methods.
old-location: debugger\getprompttext.htm
ms.assetid: 8d828cf1-991b-4c2d-882b-de56512a6737
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
req.alt-api: IDebugControl.GetPromptText,IDebugControl2.GetPromptText,IDebugControl3.GetPromptText
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
ms.keywords: IDebugControl3, GetPromptText, IDebugControl3::GetPromptText
req.iface: IDebugControl3
---

# IDebugControl3::GetPromptText method



## -description
<p>The <b>GetPromptText</b>  method returns the standard prompt text that will be prepended to the formatted output specified in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553227">OutputPrompt</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff553231">OutputPromptVaList</a> methods.</p>


## -syntax

````
HRESULT GetPromptText(
  [out, optional] PSTR   Buffer,
  [in]            ULONG  BufferSize,
  [out, optional] PULONG TextSize
);
````


## -parameters
<dl>

### -param <i>Buffer</i> [out, optional]

<dd>
<p>Receives the prompt text.  If <i>Buffer</i> is <b>NULL</b>, this information is not returned.</p>
</dd>

### -param <i>BufferSize</i> [in]

<dd>
<p>Specifies the size, in characters, of the <i>Buffer</i> buffer.</p>
</dd>

### -param <i>TextSize</i> [out, optional]

<dd>
<p>Receives the size, in characters, of the prompt text.  If <i>TextSize</i> is <b>NULL</b>, this information is not returned.</p>
</dd>
</dl>

## -returns
<p>This method can also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>S_FALSE</b></dt>
</dl><p>The method was successful.  However, the prompt text was too large to fit into the <i>Buffer</i> buffer and the text was truncated.</p>

<p> </p>

## -remarks
<p>For more information about prompting the user, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff560116">Using Input and Output</a>.</p>

<p>For more information about prompting the user, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff560116">Using Input and Output</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550508">IDebugControl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550512">IDebugControl2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550519">IDebugControl3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553227">OutputPrompt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553231">OutputPromptVaList</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugControl::GetPromptText method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
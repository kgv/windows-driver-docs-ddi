---
UID: NF.dbgeng.IDebugClient5.SetOutputMask
title: IDebugClient5::SetOutputMask
author: windows-driver-content
description: The SetOutputMask method sets the output mask for the client.
old-location: debugger\setoutputmask.htm
ms.assetid: 8fef4def-9735-4623-841b-a18995d4d403
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
req.alt-api: IDebugClient.SetOutputMask,IDebugClient2.SetOutputMask,IDebugClient3.SetOutputMask,IDebugClient4.SetOutputMask,IDebugClient5.SetOutputMask
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
ms.keywords: IDebugClient5, SetOutputMask, IDebugClient5::SetOutputMask
req.iface: IDebugClient5
---

# IDebugClient5::SetOutputMask method



## -description
<p>The <b>SetOutputMask</b> method sets the output mask for the client.</p>


## -syntax

````
HRESULT SetOutputMask(
  [in] ULONG Mask
);
````


## -parameters
<dl>

### -param <i>Mask</i> [in]

<dd>
<p>Specifies the new output mask for the client.  See <a href="https://msdn.microsoft.com/library/windows/hardware/ff541518">DEBUG_OUTPUT_XXX</a> for a description of the possible values for <i>Mask</i>.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

## -remarks
<p>For an overview of output in the debugger engine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff550971">Input and Output</a>.</p>

<p>For an overview of output in the debugger engine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff550971">Input and Output</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549827">IDebugClient</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550481">IDebugClient2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550488">IDebugClient3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550494">IDebugClient4</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550497">IDebugClient5</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548080">GetOutputMask</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556750">SetOtherOutputMask</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugClient::SetOutputMask method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
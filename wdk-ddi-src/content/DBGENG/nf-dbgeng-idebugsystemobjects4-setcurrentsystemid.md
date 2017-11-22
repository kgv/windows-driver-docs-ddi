---
UID: NF.dbgeng.IDebugSystemObjects4.SetCurrentSystemId
title: IDebugSystemObjects4::SetCurrentSystemId
author: windows-driver-content
description: The SetCurrentSystemId method makes the specified target the current target.
old-location: debugger\setcurrentsystemid.htm
ms.assetid: 95b761ff-ca78-4793-b5eb-a9ff35a963d3
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
req.alt-api: IDebugSystemObjects3.SetCurrentSystemId,IDebugSystemObjects4.SetCurrentSystemId
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
ms.keywords: IDebugSystemObjects4, SetCurrentSystemId, IDebugSystemObjects4::SetCurrentSystemId
req.iface: IDebugSystemObjects4
---

# IDebugSystemObjects4::SetCurrentSystemId method



## -description
<p>The <b>SetCurrentSystemId</b> method makes the specified target the current target.</p>


## -syntax

````
HRESULT SetCurrentSystemId(
  [in] ULONG Id
);
````


## -parameters
<dl>

### -param <i>Id</i> [in]

<dd>
<p>Specifies the engine target ID for the target that is to become the current target.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>E_NOINTERFACE</b></dt>
</dl><p>No process with the given ID was found.</p>

<p> </p>

## -remarks
<p>This method also sets the current thread and current process, and may change the current computer.</p>

<p>If the current target is changed, the callback <a href="https://msdn.microsoft.com/library/windows/hardware/ff550683">IDebugEventCallbacks::ChangeEngineState</a> will be called with the DEBUG_CES_CURRENT_THREAD bit set.</p>

<p>This method also sets the current thread and current process, and may change the current computer.</p>

<p>If the current target is changed, the callback <a href="https://msdn.microsoft.com/library/windows/hardware/ff550683">IDebugEventCallbacks::ChangeEngineState</a> will be called with the DEBUG_CES_CURRENT_THREAD bit set.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550892">IDebugSystemObjects3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550893">IDebugSystemObjects4</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541386">Debugging Session and Execution Model</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552239">Monitoring Events</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugSystemObjects3::SetCurrentSystemId method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
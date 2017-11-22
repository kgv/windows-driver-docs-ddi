---
UID: NC.ntdd8042.PI8042_KEYBOARD_INITIALIZATION_ROUTINE
title: PI8042_KEYBOARD_INITIALIZATION_ROUTINE
author: windows-driver-content
description: A PI8042_KEYBOARD_INITIALIZATION_ROUTINE-typed callback routine supplements the default initialization of a keyboard device by I8042prt.
old-location: hid\pi8042_keyboard_initialization_routine.htm
ms.assetid: bc1c82f0-f68c-433c-87f0-16c687d18557
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: hid
req.header: ntdd8042.h
req.include-header: Ntdd8042.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeyboardInitializationRoutine
req.alt-loc: ntdd8042.h
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
ms.keywords: MSFC_VirtualFibrePortAttributes, MSFC_VirtualFibrePortAttributes, *PMSFC_VirtualFibrePortAttributes
req.iface: 
---

# PI8042_KEYBOARD_INITIALIZATION_ROUTINE callback



## -description
<p>A PI8042_KEYBOARD_INITIALIZATION_ROUTINE-typed callback routine supplements the default initialization of a keyboard device by I8042prt.</p>


## -prototype

````
PI8042_KEYBOARD_INITIALIZATION_ROUTINE KeyboardInitializationRoutine;

NTSTATUS KeyboardInitializationRoutine(
  _In_  PVOID                   InitializationContext,
  _In_  PVOID                   SynchFuncContext,
  _In_  PI8042_SYNCH_READ_PORT  ReadPort,
  _In_  PI8042_SYNCH_WRITE_PORT WritePort,
  _Out_ PBOOLEAN                TurnTranslationOn
)
{ ... }
````


## -parameters
<dl>

### -param <i>InitializationContext</i> [in]

<dd>
<p>Pointer to the filter device object of the driver that supplies the callback.</p>
</dd>

### -param <i>SynchFuncContext</i> [in]

<dd>
<p>Pointer to the context for the callbacks that are pointed to by <i>ReadPort</i> and <i>Writeport.</i></p>
</dd>

### -param <i>ReadPort</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543272">PI8042_SYNCH_READ_PORT</a> callback that reads from the port.</p>
</dd>

### -param <i>WritePort</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543276">PI8042_SYNCH_WRITE_PORT</a> callback that writes to the port.</p>
</dd>

### -param <i>TurnTranslationOn</i> [out]

<dd>
<p>Specifies whether to turn translation on or off. If <i>TranslationOn</i> is <b>TRUE</b>, translation is turned on; otherwise, translation is turned off.</p>
</dd>
</dl>

## -returns
<p>A PI8042_KEYBOARD_INITIALIZATION_ROUTINE callback returns an appropriate NTSTATUS code.</p>

## -remarks
<p>An upper-level keyboard filter driver can provide a PI8042_KEYBOARD_INITIALIZATION_ROUTINE callback.</p>

<p>If an upper-level keyboard filter driver supplies an initialization callback, I8042prt calls the filter initialization callback when I8042prt initializes the keyboard. Default keyboard initialization includes the following operations: reset the keyboard, set the typematic rate and delay, and set the light-emitting diodes (LED).</p>

<p>An upper-level keyboard filter driver can provide a PI8042_KEYBOARD_INITIALIZATION_ROUTINE callback.</p>

<p>If an upper-level keyboard filter driver supplies an initialization callback, I8042prt calls the filter initialization callback when I8042prt initializes the keyboard. Default keyboard initialization includes the following operations: reset the keyboard, set the typematic rate and delay, and set the light-emitting diodes (LED).</p>

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
<dt>Ntdd8042.h (include Ntdd8042.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543272">PI8042_SYNCH_READ_PORT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543276">PI8042_SYNCH_WRITE_PORT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20PI8042_KEYBOARD_INITIALIZATION_ROUTINE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
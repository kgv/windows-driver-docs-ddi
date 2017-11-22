---
UID: NF.ntddk.DbgPrompt
title: DbgPrompt
author: windows-driver-content
description: The DbgPrompt routine displays a caller-specified user prompt string on the kernel debugger's display device and obtains a user response string.
old-location: devtest\dbgprompt.htm
ms.assetid: 4bb44aab-7032-4cc7-89e3-6ac3bee233d3
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: devtest
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DbgPrompt
req.alt-loc: NtDll.dll,NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtDll.lib (user mode); 
NtosKrnl.lib (kernel mode)
req.dll: NtDll.dll (user mode); 
NtosKrnl.exe (kernel mode)
req.irql: <= DIRQL
ms.keywords: DbgPrompt
req.iface: 
---

# DbgPrompt function



## -description
<p>The <b>DbgPrompt</b> routine displays a caller-specified user prompt string on the kernel debugger's display device and obtains a user response string.</p>


## -syntax

````
ULONG DbgPrompt(
  _In_  PCCH  Prompt,
  _Out_ PCHAR Response,
  _In_  ULONG MaximumResponseLength
);
````


## -parameters
<dl>

### -param <i>Prompt</i> [in]

<dd>
<p>A pointer to a NULL-terminated constant character string that the debugger will display as a user prompt. The maximum size of this string is 512 characters.</p>
</dd>

### -param <i>Response</i> [out]

<dd>
<p>A pointer to a character array buffer that receives the user's response, including a terminating newline character. The maximum size of this buffer is 512 characters.</p>
</dd>

### -param <i>MaximumResponseLength</i> [in]

<dd>
<p>The size, in characters, of the buffer that receives the user's response. This size is the maximum number of characters that the routine will return.</p>
</dd>
</dl>

## -returns
<p><b>DbgPrompt</b> returns the number of characters that the <i>Response</i> buffer received, including the terminating newline character. <b>DbgPrompt</b> returns zero if it receives no characters.</p>

## -remarks
<p>The <b>DbgPrompt</b> routine displays the specified prompt string on the kernel debugger's display device and then reads a line of user input text. </p>

<p>After <b>DbgPrompt</b> returns, the <i>Response</i> buffer contains the user's response, including the terminating newline character. The user response string is not NULL-terminated.</p>

<p>The following code example asks if the user wants to continue and accepts the letter "y" for yes and the letter "n" for no.</p>

<p>The <b>DbgPrompt</b> routine displays the specified prompt string on the kernel debugger's display device and then reads a line of user input text. </p>

<p>After <b>DbgPrompt</b> returns, the <i>Response</i> buffer contains the user's response, including the terminating newline character. The user response string is not NULL-terminated.</p>

<p>The following code example asks if the user wants to continue and accepts the letter "y" for yes and the letter "n" for no.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
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
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtDll.lib (user mode); </dt>
<dt>NtosKrnl.lib (kernel mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtDll.dll (user mode); </dt>
<dt>NtosKrnl.exe (kernel mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DIRQL</p>
</td>
</tr>
</table>
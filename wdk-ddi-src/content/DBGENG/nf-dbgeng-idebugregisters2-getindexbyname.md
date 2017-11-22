---
UID: NF.dbgeng.IDebugRegisters2.GetIndexByName
title: IDebugRegisters2::GetIndexByName
author: windows-driver-content
description: The GetIndexByName method returns the index of the named register.
old-location: debugger\getindexbyname.htm
ms.assetid: a012b235-ed50-4009-a7ee-01783f9e3597
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: DbgEng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugRegisters.GetIndexByName,IDebugRegisters2.GetIndexByName
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
ms.keywords: IDebugRegisters2, GetIndexByName, IDebugRegisters2::GetIndexByName
req.iface: IDebugRegisters2
---

# IDebugRegisters2::GetIndexByName method



## -description
<p>The <b>GetIndexByName</b> method returns the index of the named register.</p>


## -syntax

````
HRESULT GetIndexByName(
  [in]  PCSTR  Name,
  [out] PULONG Index
);
````


## -parameters
<dl>

### -param <i>Name</i> [in]

<dd>
<p>Specifies the name of the register whose index is requested.</p>
</dd>

### -param <i>Index</i> [out]

<dd>
<p>Receives the index of the register.</p>
</dd>
</dl>

## -returns
<p>This list does not contain all the errors that might occur.  For a list of possible errors, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff549771">HRESULT Values</a>.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>E_NOINTERFACE</b></dt>
</dl><p>The register was not found.</p>

<p> </p>

## -remarks
<p>For an overview of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550825">IDebugRegisters</a> interface and other register-related methods, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.</p>

<p>For an overview of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550825">IDebugRegisters</a> interface and other register-related methods, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.</p>

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
<dt>Dbgeng.h (include DbgEng.h)</dt>
</dl>
</td>
</tr>
</table>
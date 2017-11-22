---
UID: NS.compstui._PROPSHEETUI_GETICON_INFO
title: PROPSHEETUI_GETICON_INFO
author: windows-driver-content
description: The PROPSHEETUI_GETICON_INFO structure is used as an input parameter to an application's PFNPROPSHEETUI-typed function, when the function is called with a reason value of PROPSHEETUI_REASON_GET_ICON.
old-location: print\propsheetui_geticon_info.htm
ms.assetid: 23c06f1c-0c8f-4055-a997-1ff94c4a541e
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: compstui.h
req.include-header: Compstui.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PROPSHEETUI_GETICON_INFO
req.alt-loc: compstui.h
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
ms.keywords: PROPSHEETUI_GETICON_INFO, PROPSHEETUI_GETICON_INFO, *PPROPSHEETUI_GETICON_INFO
req.iface: 
---

# PROPSHEETUI_GETICON_INFO structure



## -description
<p>The PROPSHEETUI_GETICON_INFO structure is used as an input parameter to an application's <a href="https://msdn.microsoft.com/library/windows/hardware/ff559812">PFNPROPSHEETUI</a>-typed function, when the function is called with a reason value of PROPSHEETUI_REASON_GET_ICON.</p>


## -syntax

````
typedef struct _PROPSHEETUI_GETICON_INFO {
  WORD  cbSize;
  WORD  Flags;
  WORD  cxIcon;
  WORD  cyIcon;
  HICON hIcon;
} PROPSHEETUI_GETICON_INFO, *PPROPSHEETUI_GETICON_INFO;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd>
<p>CPSUI-supplied size, in bytes, of the PROPSHEETUI_GETICON_INFO structure.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>cxIcon</b>

<dd>
<p>CPSUI-supplied icon width, in pixels.</p>
</dd>

### -field <b>cyIcon</b>

<dd>
<p>CPSUI-supplied icon height, in pixels.</p>
</dd>

### -field <b>hIcon</b>

<dd>
<p>Receives an application-supplied icon handle. If the icon is not loaded, the member must be set to zero.</p>
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
<dt>Compstui.h (include Compstui.h)</dt>
</dl>
</td>
</tr>
</table>
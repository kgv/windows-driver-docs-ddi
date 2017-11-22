---
UID: NS.compstui._CPSUIDATABLOCK
title: CPSUIDATABLOCK
author: windows-driver-content
description: The CPSUIDATABLOCK structure is used as a parameter for the ComPropSheet function, if the function code is CPSFUNC_SET_DATABLOCK or CPSFUNC_QUERY_DATABLOCK.
old-location: print\cpsuidatablock.htm
ms.assetid: c5b488ac-dd8d-4484-81ca-b64fdf517100
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
req.alt-api: CPSUIDATABLOCK
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
ms.keywords: CPSUIDATABLOCK, CPSUIDATABLOCK, *PCPSUIDATABLOCK
req.iface: 
---

# CPSUIDATABLOCK structure



## -description
<p>The CPSUIDATABLOCK structure is used as a parameter for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546207">ComPropSheet</a> function, if the function code is <a href="https://msdn.microsoft.com/library/windows/hardware/ff547036">CPSFUNC_SET_DATABLOCK</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff546425">CPSFUNC_QUERY_DATABLOCK</a>.</p>


## -syntax

````
typedef struct _CPSUIDATABLOCK {
  DWORD  cbData;
  LPBYTE pbData;
} CPSUIDATABLOCK, *PCPSUIDATABLOCK;
````


## -struct-fields
<dl>

### -field <b>cbData</b>

<dd>
<p>Size, in bytes of the buffer pointed to by <b>pbData</b>.</p>
</dd>

### -field <b>pbData</b>

<dd>
<p>Pointer to a caller-allocated buffer.</p>
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
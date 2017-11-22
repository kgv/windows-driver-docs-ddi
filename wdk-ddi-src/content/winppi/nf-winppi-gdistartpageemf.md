---
UID: NF.winppi.GdiStartPageEMF
title: GdiStartPageEMF
author: windows-driver-content
description: The GdiStartPageEMF function performs initialization operations for a physical page of an EMF-formatted print job.
old-location: print\gdistartpageemf.htm
ms.assetid: 963c809f-da89-4f27-ba8b-3de8cdcec179
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: winppi.h
req.include-header: Winppi.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GdiStartPageEMF
req.alt-loc: Gdi32.dll,Ext-MS-Win-GDI-Internal-Desktop-L1-1-0.dll,GDI32Full.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Gdi32.Lib
req.dll: Gdi32.dll
req.irql: 
ms.keywords: GdiStartPageEMF
req.iface: 
req.product: Windows 10 or later.
---

# GdiStartPageEMF function



## -description
<p>The <b>GdiStartPageEMF</b> function performs initialization operations for a physical page of an EMF-formatted print job.</p>


## -syntax

````
BOOL GdiStartPageEMF(
   HANDLE SpoolFileHandle
);
````


## -parameters
<dl>

### -param <i>SpoolFileHandle</i> 

<dd>
<p>Caller-supplied spool file handle, obtained by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549517">GdiGetSpoolFileHandle</a>.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the function returns <b>TRUE</b>. Otherwise the function returns <b>FALSE</b>, and an error code can be obtained by calling <b>GetLastError</b>.</p>

## -remarks
<p>The <b>GdiStartPageEMF</b> function is exported by gdi32.dll for use within a print processor's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560724">PrintDocumentOnPrintProcessor</a> function.</p>

<p>A print processor must call the <b>GdiStartPageEMF</b> function each time a new physical page is to be created. It can then call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549524">GdiPlayPageEMF</a> for each document page that is to be placed on the physical page.</p>

<p>For additional information, see <a href="NULL">Using GDI Functions in Print Processors</a>.</p>

<p>The <b>GdiStartPageEMF</b> function is exported by gdi32.dll for use within a print processor's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560724">PrintDocumentOnPrintProcessor</a> function.</p>

<p>A print processor must call the <b>GdiStartPageEMF</b> function each time a new physical page is to be created. It can then call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549524">GdiPlayPageEMF</a> for each document page that is to be placed on the physical page.</p>

<p>For additional information, see <a href="NULL">Using GDI Functions in Print Processors</a>.</p>

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
<dt>Winppi.h (include Winppi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.Lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549468">GdiEndPageEMF</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20GdiStartPageEMF function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
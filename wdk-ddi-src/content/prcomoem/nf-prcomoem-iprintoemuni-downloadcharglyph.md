---
UID: NF.prcomoem.IPrintOemUni.DownloadCharGlyph
title: IPrintOemUni::DownloadCharGlyph
author: windows-driver-content
description: The IPrintOemUni::DownloadCharGlyph method enables a rendering plug-in for Unidrv to send a character glyph for a specified soft font to the printer.
old-location: print\iprintoemuni_downloadcharglyph.htm
ms.assetid: 1ce7ebaa-759e-418a-af07-e530b1102567
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: prcomoem.h
req.include-header: Prcomoem.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPrintOemUni.DownloadCharGlyph
req.alt-loc: prcomoem.h
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
ms.keywords: IPrintOemUni, DownloadCharGlyph, IPrintOemUni::DownloadCharGlyph
req.iface: IPrintOemUni
req.product: Windows 10 or later.
---

# IPrintOemUni::DownloadCharGlyph method



## -description
<p>The <code>IPrintOemUni::DownloadCharGlyph</code> method enables a rendering plug-in for Unidrv to send a character glyph for a specified soft font to the printer.</p>


## -syntax

````
HRESULT DownloadCharGlyph(
        PDEVOBJ     pdevobj,
        PUNIFONTOBJ pUFObj,
        HGLYPH      hGlyph,
        PDWORD      pdwWidth,
  [out] DWORD       *pdwResult
);
````


## -parameters
<dl>

### -param <i>pdevobj</i> 

<dd>
<p>Caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff547573">DEVOBJ</a> structure.</p>
</dd>

### -param <i>pUFObj</i> 

<dd>
<p>Caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563590">UNIFONTOBJ</a> structure.</p>
</dd>

### -param <i>hGlyph</i> 

<dd>
<p>Caller-supplied glyph handle.</p>
</dd>

### -param <i>pdwWidth</i> 

<dd>
<p>Caller-supplied pointer to receive the method-supplied width of the character.</p>
</dd>

### -param <i>pdwResult</i> [out]

<dd>
<p>Receives a method-supplied value representing the amount of printer memory, in bytes, required to store the character glyph. If the operation fails, the returned value should be zero.</p>
</dd>
</dl>

## -returns
<p>The method must return one of the following values.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The operation succeeded.</p><dl>
<dt><b>E_FAIL</b></dt>
</dl><p>The operation failed</p><dl>
<dt><b>E_NOTIMPL</b></dt>
</dl><p>The method is not implemented.</p>

<p> </p>

## -remarks
<p>The <code>IPrintOemUni::DownloadCharGlyph</code> method is used for supporting soft fonts on printers that do not accept <a href="wdkgloss.p#wdkgloss.pcl#wdkgloss.pcl"><i>PCL</i></a> commands. Its purpose is to enable a rendering plug-in to send a character glyph to the printer.</p>

<p>If a rendering plug-in implements the  <code>IPrintOemUni::DownloadCharGlyph</code> method, Unidrv calls the method immediately after sending the command string specified by the CmdSetCharCode command entry, which is contained in the printer's <a href="wdkgloss.g#wdkgloss.generic_printer_description__gpd_#wdkgloss.generic_printer_description__gpd_"><i>GPD</i></a> file. (GPD files are described in <a href="NULL">Microsoft Universal Printer Driver</a>.) The method should do the following:</p>

<p>Call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563594">UNIFONTOBJ_GetInfo</a> function to obtain the glyph image specified by <i>hGlyph</i>.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff553138">IPrintOemDriverUni::DrvWriteSpoolBuf</a> to send the glyph to the printer.</p>

<p>Call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563594">UNIFONTOBJ_GetInfo</a> function again to obtain the glyph's width, then store the width in the address pointed to by <i>pdwWidth</i>. </p>

<p>Return the amount of printer memory required to store the glyph by placing it in the location specified by <i>pdwResult</i>.</p>

<p>The <code>IPrintOemUni::DownloadCharGlyph</code> method is optional. If a rendering plug-in implements this method, the plug-in's <a href="https://msdn.microsoft.com/library/windows/hardware/ff554253">IPrintOemUni::GetImplementedMethod</a> method must return S_OK when it receives "DownloadCharGlyph" as input.</p>

<p>If you implement the <code>IPrintOemUni::DownloadCharGlyph</code> method, you must also implement the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554242">IPrintOemUni::DownloadFontHeader</a> method.</p>

<p>For additional information see <a href="NULL">Customized Font Management</a>.</p>

<p>The <code>IPrintOemUni::DownloadCharGlyph</code> method is used for supporting soft fonts on printers that do not accept <a href="wdkgloss.p#wdkgloss.pcl#wdkgloss.pcl"><i>PCL</i></a> commands. Its purpose is to enable a rendering plug-in to send a character glyph to the printer.</p>

<p>If a rendering plug-in implements the  <code>IPrintOemUni::DownloadCharGlyph</code> method, Unidrv calls the method immediately after sending the command string specified by the CmdSetCharCode command entry, which is contained in the printer's <a href="wdkgloss.g#wdkgloss.generic_printer_description__gpd_#wdkgloss.generic_printer_description__gpd_"><i>GPD</i></a> file. (GPD files are described in <a href="NULL">Microsoft Universal Printer Driver</a>.) The method should do the following:</p>

<p>Call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563594">UNIFONTOBJ_GetInfo</a> function to obtain the glyph image specified by <i>hGlyph</i>.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff553138">IPrintOemDriverUni::DrvWriteSpoolBuf</a> to send the glyph to the printer.</p>

<p>Call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563594">UNIFONTOBJ_GetInfo</a> function again to obtain the glyph's width, then store the width in the address pointed to by <i>pdwWidth</i>. </p>

<p>Return the amount of printer memory required to store the glyph by placing it in the location specified by <i>pdwResult</i>.</p>

<p>The <code>IPrintOemUni::DownloadCharGlyph</code> method is optional. If a rendering plug-in implements this method, the plug-in's <a href="https://msdn.microsoft.com/library/windows/hardware/ff554253">IPrintOemUni::GetImplementedMethod</a> method must return S_OK when it receives "DownloadCharGlyph" as input.</p>

<p>If you implement the <code>IPrintOemUni::DownloadCharGlyph</code> method, you must also implement the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554242">IPrintOemUni::DownloadFontHeader</a> method.</p>

<p>For additional information see <a href="NULL">Customized Font Management</a>.</p>

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
<dt>Prcomoem.h (include Prcomoem.h)</dt>
</dl>
</td>
</tr>
</table>
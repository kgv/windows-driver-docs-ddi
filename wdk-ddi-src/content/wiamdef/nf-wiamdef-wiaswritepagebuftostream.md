---
UID: NF.wiamdef.wiasWritePageBufToStream
title: wiasWritePageBufToStream
author: windows-driver-content
description: The wiasWritePageBufToStream function writes the contents of a temporary page buffer to the IStream interface provided by the application.
old-location: image\wiaswritepagebuftostream.htm
ms.assetid: f8f8ac2a-705e-426c-8c4a-00581b8d1dfe
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: image
req.header: wiamdef.h
req.include-header: Wiamdef.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: wiasWritePageBufToStream
req.alt-loc: Wiaservc.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wiaservc.lib
req.dll: Wiaservc.dll
req.irql: 
ms.keywords: wiasWritePageBufToStream
req.iface: 
req.product: Windows 10 or later.
---

# wiasWritePageBufToStream function



## -description
<p>The <b>wiasWritePageBufToStream</b> function writes the contents of a temporary page buffer to the <b>IStream</b> interface provided by the application.</p>


## -syntax

````
HRESULT _stdcall wiasWritePageBufToStream(
  _In_ PMINIDRV_TRANSFER_CONTEXT pmdtc,
  _In_ IStream                   *pstream
);
````


## -parameters
<dl>

### -param <i>pmdtc</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff545250">MINIDRV_TRANSFER_CONTEXT</a> structure.</p>
</dd>

### -param <i>pstream</i> [in]

<dd>
<p>Pointer to the <b>IStream</b> data stream provided by the application. The <b>IStream</b> interface is described in the Microsoft Windows SDK documentation.</p>
</dd>
</dl>

## -returns
<p>On success, the function returns S_OK. If the function fails, it returns a standard COM error or one of the WIA_ERROR_<i>XXX</i> errors (described in the Windows SDK documentation).</p>

## -remarks
<p>The function writes data from a temporary page buffer that is allocated by a minidriver to the image data stream provided by the calling application. Minidrivers typically call this function after acquiring a page of data for which the minidriver allocated a temporary buffer.</p>

<p>This function is similar to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549473">wiasWriteBufToFile</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff549484">wiasWritePageBufToFile</a>. The <b>wiasWriteBufToFile </b>function can be used to write a buffer of image data to any type of image file. The <b>wiasWritePageBufToFile</b> function can be used to write a page of image data to a multipage TIFF file with all appropriate tags and image file directory (IFD) entries. If the driver intends to write this multipage TIFF file data to a stream, it would call <b>wiasWritePageBufToStream</b>.</p>

<p>The function writes data from a temporary page buffer that is allocated by a minidriver to the image data stream provided by the calling application. Minidrivers typically call this function after acquiring a page of data for which the minidriver allocated a temporary buffer.</p>

<p>This function is similar to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549473">wiasWriteBufToFile</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff549484">wiasWritePageBufToFile</a>. The <b>wiasWriteBufToFile </b>function can be used to write a buffer of image data to any type of image file. The <b>wiasWritePageBufToFile</b> function can be used to write a page of image data to a multipage TIFF file with all appropriate tags and image file directory (IFD) entries. If the driver intends to write this multipage TIFF file data to a stream, it would call <b>wiasWritePageBufToStream</b>.</p>

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
<dt>Wiamdef.h (include Wiamdef.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wiaservc.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Wiaservc.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545250">MINIDRV_TRANSFER_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549473">wiasWriteBufToFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549484">wiasWritePageBufToFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [image\image]:%20wiasWritePageBufToStream function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
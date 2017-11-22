---
UID: NF.wudfddi.IWDFIoTarget.FormatRequestForRead
title: IWDFIoTarget::FormatRequestForRead
author: windows-driver-content
description: The FormatRequestForRead method formats an I/O request object for a read operation.
old-location: wdf\iwdfiotarget_formatrequestforread.htm
ms.assetid: 8a1b61c8-8b85-4224-ae20-3788eb0babe4
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: Wudfddi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.5
req.alt-api: IWDFIoTarget.FormatRequestForRead
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: <= DISPATCH_LEVEL
ms.keywords: IWDFIoTarget, FormatRequestForRead, IWDFIoTarget::FormatRequestForRead
req.iface: IWDFIoTarget
req.product: Windows 10 or later.
---

# IWDFIoTarget::FormatRequestForRead method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>FormatRequestForRead</b> method formats an I/O request object for a read operation.</p>


## -syntax

````
HRESULT FormatRequestForRead(
  [in]           IWDFIoRequest     *pRequest,
  [in, optional] IWDFFile          *pFile,
  [in, optional] IWDFMemory        *pOutputMemory,
  [in, optional] PWDFMEMORY_OFFSET pOutputMemoryOffset,
  [in, optional] PLONGLONG         DeviceOffset
);
````


## -parameters
<dl>

### -param <i>pRequest</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558985">IWDFIoRequest</a> interface for the request object to format. </p>
</dd>

### -param <i>pFile</i> [in, optional]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558912">IWDFFile</a> interface for the file object that is associated with the read request. For the default I/O target, this parameter must be non-NULL.</p>
</dd>

### -param <i>pOutputMemory</i> [in, optional]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559249">IWDFMemory</a> interface that is used to access the buffer that is used for the read request. This parameter is optional.</p>
</dd>

### -param <i>pOutputMemoryOffset</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561398">WDFMEMORY_OFFSET</a> structure that describes the output memory offset that is used for the read. This parameter is optional.</p>
</dd>

### -param <i>DeviceOffset</i> [in, optional]

<dd>
<p>A pointer to the device offset that is used for the read. This parameter is optional.</p>
</dd>
</dl>

## -returns
<p><b>FormatRequestForRead</b> returns S_OK if the operation succeeds. Otherwise, this method returns one of the error codes that are defined in Winerror.h. </p>

<p>For a code example of how to use the <b>FormatRequestForRead</b> method, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff557021">IWDFDevice::CreateRequest</a>.</p>

## -remarks


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
<p>End of support</p>
</th>
<td width="70%">
<p>Unavailable in UMDF 2.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.5</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559170">IWDFIoTarget</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558912">IWDFFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558985">IWDFIoRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559249">IWDFMemory</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561398">WDFMEMORY_OFFSET</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFIoTarget::FormatRequestForRead method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.wudfddi.IWDFIoTarget2.FormatRequestForSetInformation
title: IWDFIoTarget2::FormatRequestForSetInformation
author: windows-driver-content
description: The FormatRequestForSetInformation method formats an I/O request to set information about a file, but it does not send the request to an I/O target.
old-location: wdf\iwdfiotarget2_formatrequestforsetinformation.htm
ms.assetid: 2bfdc5c6-da5a-43c1-9165-02d6c448a690
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
req.umdf-ver: 1.9
req.alt-api: IWDFIoTarget2.FormatRequestForSetInformation
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
ms.keywords: IWDFIoTarget2, FormatRequestForSetInformation, IWDFIoTarget2::FormatRequestForSetInformation
req.iface: IWDFIoTarget2
req.product: Windows 10 or later.
---

# IWDFIoTarget2::FormatRequestForSetInformation method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>FormatRequestForSetInformation</b> method formats an I/O request to set information about a file, but it does not send the request to an I/O target.</p>


## -syntax

````
HRESULT FormatRequestForSetInformation(
  [in]           IWDFIoRequest              *pRequest,
  [in]           WDF_FILE_INFORMATION_CLASS InformationClass,
  [in, optional] IWDFFile                   *pFile,
  [in, optional] IWDFMemory                 *pInformationMemory,
  [in, optional] PWDFMEMORY_OFFSET          pInformationMemoryOffset
);
````


## -parameters
<dl>

### -param <i>pRequest</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558985">IWDFIoRequest</a> interface of the request object that represents the I/O request. </p>
</dd>

### -param <i>InformationClass</i> [in]

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff561405">WDF_FILE_INFORMATION_CLASS</a>-typed value that specifies the type of information to set.</p>
</dd>

### -param <i>pFile</i> [in, optional]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558912">IWDFFile</a> interface of the file object that is associated with the I/O request. This parameter is required for local and remote <a href="wdf.using_i_o_targets_in_umdf">I/O targets</a>, and is optional (can be <b>NULL</b>) for file handle I/O targets.</p>
</dd>

### -param <i>pInformationMemory</i> [in, optional]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559249">IWDFMemory</a> interface of a memory object. This object represents the input buffer, which contains driver-supplied file information that the <i>InformationClass</i> parameter specifies. This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>pInformationMemoryOffset</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561398">WDFMEMORY_OFFSET</a> structure that supplies optional byte offset and length values. The framework uses these values to determine the beginning address and length, within the input buffer, for the data transfer. If this pointer is <b>NULL</b>, the data transfer begins at the beginning of the input buffer, and the transfer size is the buffer size.</p>
</dd>
</dl>

## -returns
<p><b>FormatRequestForSetInformation</b> returns S_OK if the operation succeeds. Otherwise, the method might return the following value:</p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p>The framework was unable to allocate memory.</p>

<p> </p>

<p>This method might return one of the other values that Winerror.h contains.</p>

## -remarks
<p>Use the <b>FormatRequestForSetInformation</b> method, followed by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559149">IWDFIoRequest::Send</a> method, to send requests either synchronously or asynchronously to an <a href="wdf.using_i_o_targets_in_umdf">I/O target</a>. </p>

<p>The following code example is part of an <a href="https://msdn.microsoft.com/library/windows/hardware/ff556847">IQueueCallbackDefaultIoHandler::OnDefaultIoHandler</a> callback function. If the callback function receives a set information request, it sends the request to the device's default I/O target.</p>

<p>Use the <b>FormatRequestForSetInformation</b> method, followed by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559149">IWDFIoRequest::Send</a> method, to send requests either synchronously or asynchronously to an <a href="wdf.using_i_o_targets_in_umdf">I/O target</a>. </p>

<p>The following code example is part of an <a href="https://msdn.microsoft.com/library/windows/hardware/ff556847">IQueueCallbackDefaultIoHandler::OnDefaultIoHandler</a> callback function. If the callback function receives a set information request, it sends the request to the device's default I/O target.</p>

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
<p>1.9</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559175">IWDFIoTarget2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559184">IWDFIoTarget2::FormatRequestForQueryInformation</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFIoTarget2::FormatRequestForSetInformation method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
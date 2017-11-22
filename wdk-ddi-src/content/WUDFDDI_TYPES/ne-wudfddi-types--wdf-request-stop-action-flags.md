---
UID: NE.wudfddi_types._WDF_REQUEST_STOP_ACTION_FLAGS
title: WDF_REQUEST_STOP_ACTION_FLAGS
author: windows-driver-content
description: The WDF_REQUEST_STOP_ACTION_FLAGS enumeration contains values that identify the state of a stop action request in a call to the driver's IQueueCallbackIoStop::OnIoStop method.
old-location: wdf\wdf_request_stop_action_flags_umdf.htm
ms.assetid: b9e3ea22-be24-4f36-abde-339495b9ed1c
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi_types.h
req.include-header: Wudfddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WDF_REQUEST_STOP_ACTION_FLAGS
req.alt-loc: Wudfddi_types.h
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
ms.keywords: WRITE_REGISTER_USHORT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_REQUEST_STOP_ACTION_FLAGS enumeration



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>
      The <a href="https://msdn.microsoft.com/library/windows/hardware/ff561465">WDF_REQUEST_STOP_ACTION_FLAGS</a> enumeration contains values that identify the state of a stop action request in a call to the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff556871">IQueueCallbackIoStop::OnIoStop</a> method.</p>


## -syntax

````
typedef enum _WDF_REQUEST_STOP_ACTION_FLAGS { 
  WdfRequestStopActionInvalid      = 0x00000000,
  WdfRequestStopActionSuspend      = 0x00000001,
  WdfRequestStopActionPurge        = 0x00000002,
  WdfRequestStopRequestCancelable  = 0x10000000
} WDF_REQUEST_STOP_ACTION_FLAGS;
````


## -enum-fields
<dl>

### -field <a id="WdfRequestStopActionInvalid"></a><a id="wdfrequeststopactioninvalid"></a><a id="WDFREQUESTSTOPACTIONINVALID"></a><b>WdfRequestStopActionInvalid</b>

<dd>
<p>If this value is set to 1, the request is invalid.</p>
</dd>

### -field <a id="WdfRequestStopActionSuspend"></a><a id="wdfrequeststopactionsuspend"></a><a id="WDFREQUESTSTOPACTIONSUSPEND"></a><b>WdfRequestStopActionSuspend</b>

<dd>
<p>If this value is set to 1, the device is suspended.</p>
</dd>

### -field <a id="WdfRequestStopActionPurge"></a><a id="wdfrequeststopactionpurge"></a><a id="WDFREQUESTSTOPACTIONPURGE"></a><b>WdfRequestStopActionPurge</b>

<dd>
<p>If this value is set to 1, the device and queue are removed.</p>
</dd>

### -field <a id="WdfRequestStopRequestCancelable"></a><a id="wdfrequeststoprequestcancelable"></a><a id="WDFREQUESTSTOPREQUESTCANCELABLE"></a><b>WdfRequestStopRequestCancelable</b>

<dd>
<p>If this value is set to 1, the request is marked as cancelable.</p>
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
<dt>Wudfddi_types.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556871">IQueueCallbackIoStop::OnIoStop</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_REQUEST_STOP_ACTION_FLAGS enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
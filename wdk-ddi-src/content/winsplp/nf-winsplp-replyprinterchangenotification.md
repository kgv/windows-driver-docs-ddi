---
UID: NF.winsplp.ReplyPrinterChangeNotification
title: ReplyPrinterChangeNotification
author: windows-driver-content
description: The print spooler's ReplyPrinterChangeNotification function allows a print provider to update the spooler's database of print queue events associated with a notification handle, and to notify the client that print queue events have occurred.
old-location: print\replyprinterchangenotification.htm
ms.assetid: 0b5378fa-ab1d-453f-b976-f6cd0d4247de
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: Winsplp.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ReplyPrinterChangeNotification
req.alt-loc: Spoolss.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Spoolss.lib
req.dll: Spoolss.dll
req.irql: 
ms.keywords: ReplyPrinterChangeNotification
req.iface: 
req.product: Windows 10 or later.
---

# ReplyPrinterChangeNotification function



## -description
<p>The print spooler's <code>ReplyPrinterChangeNotification</code> function allows a print provider to update the spooler's database of print queue events associated with a notification handle, and to notify the client that print queue events have occurred.</p>


## -syntax

````
BOOL ReplyPrinterChangeNotification(
  _In_      HANDLE hNotify,
            DWORD  fdwFlags,
  _Out_opt_ PDWORD pdwResult,
  _In_opt_  PVOID  pPrinterNotifyInfo
);
````


## -parameters
<dl>

### -param <i>hNotify</i> [in]

<dd>
<p>Caller-supplied handle. This handle must have been previously received as the <i>hNotify</i> input to the print provider's <a href="https://msdn.microsoft.com/library/windows/hardware/ff548837">FindFirstPrinterChangeNotification</a> function.</p>
</dd>

### -param <i>fdwFlags</i> 

<dd>
<p>One or more caller-supplied PRINTER_CHANGE_-prefixed flags, listed in the Microsoft Windows SDK documentation's description of <b>FindNextPrinterChangeNotification</b>.</p>
</dd>

### -param <i>pdwResult</i> [out, optional]

<dd>
<p>Optional. If not <b>NULL</b>, it receives spooler-supplied PRINTER_NOTIFY_INFO-prefixed flags indicating results of updating the supplied information.</p>
</dd>

### -param <i>pPrinterNotifyInfo</i> [in, optional]

<dd>
<p>Optional. Caller-supplieid address of a PRINTER_NOTIFY_INFO structure (described in the Windows SDK documentation). Can be <b>NULL</b> if no new notification information is being added.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the function returns <b>TRUE</b>. Otherwise the function returns <b>FALSE</b>. The caller can obtain an error code by calling <b>GetLastError</b>.</p>

## -remarks
<p>Print providers that do not support polling (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff548837">FindFirstPrinterChangeNotification</a>) must notify the spooler of the occurrence of any events represented by the PRINTER_CHANGE_-prefixed flags received by the provider's <b>FindFirstPrinterChangeNotification</b> function. When an event occurs, the print provider can call <code>ReplyPrinterChangeNotification</code> to inform the spooler of the event and to supply information associated with the event. The spooler keeps track of this event information, for each notification handle, and delivers the information to an application when the application calls <b>FindNextPrinterChangeNotification</b> (described in the Windows SDK documentation).</p>

<p>When a print provider calls <code>ReplyPrinterChangeNotification</code>, it must identify the event that has occurred by setting a PRINTER_CHANGE_-prefixed flag in <i>fwdFlags</i> or by using <i>pPrinterNotifyInfo</i> to return a PRINTER_NOTIFY_INFO structure. (Use the flags listed in the Windows SDK documentation's description of <b>FindNextPrinterChangeNotification</b>--not the flags listed in the Windows SDK documentation's description of <b>FindFirstPrinterChangeNotification</b>.)</p>

<p>Calling <code>ReplyPrinterChangeNotification</code> causes the spooler to signal the client application that a print queue event has occurred. This happens even if the provider supplies <b>NULL</b> for <i>pPrinterNotifyInfo</i>. To update the spooler's record of print queue changes without causing the client to be notified, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff559739">PartialReplyPrinterChangeNotification</a>. It is common to call <b>PartialReplyPrinterChangeNotification</b> several times to update the spooler's database, then to call <code>ReplyPrinterChangeNotification</code> to notify the client that changes have occurred.</p>

<p>For additional information, see <a href="NULL">Supporting Printer Change Notifications</a>.</p>

<p>Print providers that do not support polling (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff548837">FindFirstPrinterChangeNotification</a>) must notify the spooler of the occurrence of any events represented by the PRINTER_CHANGE_-prefixed flags received by the provider's <b>FindFirstPrinterChangeNotification</b> function. When an event occurs, the print provider can call <code>ReplyPrinterChangeNotification</code> to inform the spooler of the event and to supply information associated with the event. The spooler keeps track of this event information, for each notification handle, and delivers the information to an application when the application calls <b>FindNextPrinterChangeNotification</b> (described in the Windows SDK documentation).</p>

<p>When a print provider calls <code>ReplyPrinterChangeNotification</code>, it must identify the event that has occurred by setting a PRINTER_CHANGE_-prefixed flag in <i>fwdFlags</i> or by using <i>pPrinterNotifyInfo</i> to return a PRINTER_NOTIFY_INFO structure. (Use the flags listed in the Windows SDK documentation's description of <b>FindNextPrinterChangeNotification</b>--not the flags listed in the Windows SDK documentation's description of <b>FindFirstPrinterChangeNotification</b>.)</p>

<p>Calling <code>ReplyPrinterChangeNotification</code> causes the spooler to signal the client application that a print queue event has occurred. This happens even if the provider supplies <b>NULL</b> for <i>pPrinterNotifyInfo</i>. To update the spooler's record of print queue changes without causing the client to be notified, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff559739">PartialReplyPrinterChangeNotification</a>. It is common to call <b>PartialReplyPrinterChangeNotification</b> several times to update the spooler's database, then to call <code>ReplyPrinterChangeNotification</code> to notify the client that changes have occurred.</p>

<p>For additional information, see <a href="NULL">Supporting Printer Change Notifications</a>.</p>

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
<dt>Winsplp.h (include Winsplp.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Spoolss.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Spoolss.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548837">FindFirstPrinterChangeNotification</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559739">PartialReplyPrinterChangeNotification</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20ReplyPrinterChangeNotification function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
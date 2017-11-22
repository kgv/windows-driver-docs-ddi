---
UID: NF.ucmtcpciportcontroller.UcmTcpciPortControllerSetHardwareRequestQueue
title: UcmTcpciPortControllerSetHardwareRequestQueue
author: windows-driver-content
description: Assigns a framework queue object to which the UcmTcpciCx dispatches hardware requests for the port controller.
old-location: buses\ucmtcpciportcontrollersethardwarerequestqueue.htm
ms.assetid: 47142adb-4d22-41eb-b455-93409bbffffb
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: usbref
req.header: ucmtcpciportcontroller.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: UcmTcpciPortControllerSetHardwareRequestQueue
req.alt-loc: ucmtcpciportcontroller.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: UcmTcpciPortControllerSetHardwareRequestQueue
req.iface: 
req.product: Windows 10 or later.
---

# UcmTcpciPortControllerSetHardwareRequestQueue function



## -description
<p>

                Assigns a framework queue object to which the UcmTcpciCx dispatches hardware requests for the port controller.</p>


## -syntax

````
VOID UcmTcpciPortControllerSetHardwareRequestQueue(
   UCMTCPCIPORTCONTROLLER PortControllerObject,
   WDFQUEUE               HardwareRequestQueue
);
````


## -parameters
<dl>

### -param <i>PortControllerObject</i> 

<dd>
<p>Handle to the port controller object that the client driver received in the previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/mt805844">UcmTcpciPortControllerCreate</a>.</p>
</dd>

### -param <i>HardwareRequestQueue</i> 

<dd>
<p>A handle to the framework queue object to assign.</p>
</dd>
</dl>

## -returns
<p>This method does not return a value.</p>

## -remarks
<p>The client driver must call <b>UcmTcpciPortControllerSetHardwareRequestQueue</b> after creating the port controller object. The driver must call this method only once before calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt805846">UcmTcpciPortControllerStart</a>.</p>

<p>The parent of the queue object is the port controller object. 
</p>

<p>A client driver may choose to use the same queue across multiple port controller objects. However, in that case the driver must make sure that the port controller objects do not outlive the queue object. The queue object must be deleted only after all the port controllers have been stopped. UcmTcpciCx guarantees  that only one request is processed in the queue at a time per port controller object.</p>

<p>The client driver must call <b>UcmTcpciPortControllerSetHardwareRequestQueue</b> after creating the port controller object. The driver must call this method only once before calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt805846">UcmTcpciPortControllerStart</a>.</p>

<p>The parent of the queue object is the port controller object. 
</p>

<p>A client driver may choose to use the same queue across multiple port controller objects. However, in that case the driver must make sure that the port controller objects do not outlive the queue object. The queue object must be deleted only after all the port controllers have been stopped. UcmTcpciCx guarantees  that only one request is processed in the queue at a time per port controller object.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ucmtcpciportcontroller.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt805844">UcmTcpciPortControllerCreate</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20UcmTcpciPortControllerSetHardwareRequestQueue method%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
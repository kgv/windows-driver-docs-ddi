---
UID: NF:ufxclient.UfxDeviceNotifySuspend
title: UfxDeviceNotifySuspend function
author: windows-driver-content
description: Notifies UFX about a USB bus suspend event.
old-location: buses\ufxdevicenotifysuspend.htm
old-project: usbref
ms.assetid: 80786A5A-E585-4092-814F-B940DD6967C6
ms.author: windowsdriverdev
ms.date: 3/29/2018
ms.keywords: UfxDeviceNotifySuspend, UfxDeviceNotifySuspend method [Buses], buses.ufxdevicenotifysuspend, ufxclient/UfxDeviceNotifySuspend
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ufxclient.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: DISPATCH_LEVEL
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	COM
api_location:
-	ufxclient.h
api_name:
-	UfxDeviceNotifySuspend
product:
- Windows
targetos: Windows
req.typenames: UFX_HARDWARE_FAILURE_CONTEXT, *PUFX_HARDWARE_FAILURE_CONTEXT
req.product: Windows 10 or later.
---

# UfxDeviceNotifySuspend function


## -description


Notifies UFX about a USB bus suspend event.


## -parameters




### -param UfxDevice [in]

A handle to a UFX device object that the driver created by calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt187951">UfxDeviceCreate</a>.


## -returns



This method does not return a value.




## -remarks



The client driver calls <b>UfxDeviceNotifySuspend</b> when it receives a bus suspend event. The default endpoint should be reset on a bus suspend.  The device should move to a low power mode.

The client driver typically calls <b>UfxDeviceNotifySuspend</b> from its <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> callback function.  The following example shows how to handle a suspend event.

<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>    case DeviceEventSuspend:
        if (!ControllerContext-&gt;Suspended) {
            ControllerContext-&gt;Suspended = TRUE;
            UfxDeviceNotifySuspend(ControllerContext-&gt;UfxDevice);
        }
        break;
</pre>
</td>
</tr>
</table></span></div>



---
UID: NF.storport.StorPortDeviceBusy
title: StorPortDeviceBusy
author: windows-driver-content
description: The StorPortDeviceBusy routine notifies the port driver that the specified logical unit is currently busy, handling outstanding requests.
old-location: storage\storportdevicebusy.htm
ms.assetid: 9b774f05-f2f6-4148-8fee-0efe209f7e4d
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortDeviceBusy
req.alt-loc: Storport.lib,Storport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Storport.lib
req.dll: 
req.irql: 
ms.keywords: StorPortDeviceBusy
req.iface: 
req.product: Windows 10 or later.
---

# StorPortDeviceBusy function



## -description
<p>The <b>StorPortDeviceBusy</b> routine notifies the port driver that the specified logical unit is currently busy, handling outstanding requests. </p>


## -syntax

````
STORPORT_API BOOLEAN StorPortDeviceBusy(
  _In_ PVOID HwDeviceExtension,
  _In_ UCHAR PathId,
  _In_ UCHAR TargetId,
  _In_ UCHAR Lun,
  _In_ ULONG RequestsToComplete
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension. This is a per HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the mapped access ranges for the HBA. This area is available to the miniport driver immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff567108">StorPortInitialize</a>. The port driver frees this memory when it removes the device. </p>
</dd>

### -param <i>PathId</i> [in]

<dd>
<p>Identifies the SCSI bus. </p>
</dd>

### -param <i>TargetId</i> [in]

<dd>
<p>Identifies the target controller or device on the given buses. </p>
</dd>

### -param <i>Lun</i> [in]

<dd>
<p>Identifies the logical unit for the given target controller or device. </p>
</dd>

### -param <i>RequestsToComplete</i> [in]

<dd>
<p>Indicates the number of requests that the logical unit must complete before resuming I/O requests to the miniport driver. If <i>RequestsToComplete</i> is greater than the number of currently outstanding requests, the Storport driver will complete all outstanding requests to the logical unit before resuming requests.</p>
</dd>
</dl>

## -returns
<p><b>StorPortDeviceBusy</b> returns <b>TRUE</b> if the miniport driver succeeded in notifying the port driver, <b>FALSE</b> if not.</p>

## -remarks
<p>No error log is generated when a device is busy. </p>

<p>The port driver will not issue any new requests to the logical unit until the logical unit's queue has been drained to a sufficient level where processing can continue.</p>

<p>No error log is generated when a device is busy. </p>

<p>The port driver will not issue any new requests to the logical unit until the logical unit's queue has been drained to a sufficient level where processing can continue.</p>

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
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Storport.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567041">StorPortBusy</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567489">StorPortReady</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortDeviceBusy routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.srb.ScsiPortCompleteRequest
title: ScsiPortCompleteRequest
author: windows-driver-content
description: The ScsiPortCompleteRequest routine completes all of the active requests for the given SCSI bus, controller, or LU, including a request being processed by the calling miniport driver routine.Note  The SCSI port driver and SCSI miniport driver models may be altered or unavailable in the future. Instead, we recommend using the Storport driver and Storport miniport driver models.
old-location: storage\scsiportcompleterequest.htm
ms.assetid: 9cd17a86-6652-414d-a80d-2e61c0ac99b6
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: srb.h
req.include-header: Miniport.h, Scsi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ScsiPortCompleteRequest
req.alt-loc: Scsiport.lib,Scsiport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Scsiport.lib
req.dll: 
req.irql: 
ms.keywords: ScsiPortCompleteRequest
req.iface: 
req.product: Windows 10 or later.
---

# ScsiPortCompleteRequest function



## -description
<p>The <b>ScsiPortCompleteRequest</b> routine completes all of the active requests for the given SCSI bus, controller, or LU, including a request being processed by the calling miniport driver routine.</p>


## -syntax

````
VOID ScsiPortCompleteRequest(
  _In_ PVOID HwDeviceExtension,
  _In_ UCHAR PathId,
  _In_ UCHAR TargetId,
  _In_ UCHAR Lun,
  _In_ UCHAR SrbStatus
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>Pointer to the hardware device extension. This is a per-HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the HBA's mapped access ranges. This area is available to the miniport driver in the <b>DeviceExtension-&gt;HwDeviceExtension</b> member of the HBA's device object immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff564645">ScsiPortInitialize</a>. The port driver frees this memory when it removes the device. </p>
</dd>

### -param <i>PathId</i> [in]

<dd>
<p>Identifies the SCSI bus; SP_UNTAGGED indicates all buses controlled by the HBA.</p>
</dd>

### -param <i>TargetId</i> [in]

<dd>
<p>Identifies the target controller or device on the given buses; SP_UNTAGGED indicates all targets on the bus.</p>
</dd>

### -param <i>Lun</i> [in]

<dd>
<p>Identifies the logical unit for the given target controller or device; SP_UNTAGGED indicates all logical units for the given target controllers on the given buses.</p>
</dd>

### -param <i>SrbStatus</i> [in]

<dd>
<p>Specifies the completion status to be set in the <b>SrbStatus </b>member of each SRB.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>ScsiPortCompleteRequest</b> can be called to complete outstanding requests after a bus reset, a device reset, or an abort, rather than calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff564657">ScsiPortNotification</a> for each outstanding request individually. After calling <b>ScsiPortCompleteRequest</b>, do not also call <b>ScsiPortNotification</b>. </p>

<p><b>ScsiPortCompleteRequest</b> can be called to complete outstanding requests after a bus reset, a device reset, or an abort, rather than calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff564657">ScsiPortNotification</a> for each outstanding request individually. After calling <b>ScsiPortCompleteRequest</b>, do not also call <b>ScsiPortNotification</b>. </p>

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
<dt>Srb.h (include Miniport.h or Scsi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Scsiport.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565393">SCSI_REQUEST_BLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564657">ScsiPortNotification</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ScsiPortCompleteRequest routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
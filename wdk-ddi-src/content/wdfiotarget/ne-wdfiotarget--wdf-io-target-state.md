---
UID: NE.wdfiotarget._WDF_IO_TARGET_STATE
title: WDF_IO_TARGET_STATE
author: windows-driver-content
description: The WDF_IO_TARGET_STATE enumeration specifies the states that an I/O target can be in.
old-location: wdf\wdf_io_target_state.htm
ms.assetid: 0189a83d-da46-49f1-99b8-8fb920009804
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfiotarget.h
req.include-header: Wdf.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 1.11
req.alt-api: WDF_IO_TARGET_STATE
req.alt-loc: wdfiotarget.h,wudfddi_types.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY, WDF_IO_QUEUE_FORWARD_PROGRESS_POLICY, *PWDF_IO_QUEUE_FORWARD_PROGRESS_POLICY
req.iface: 
req.product: Windows 10 or later.
---

# WDF_IO_TARGET_STATE enumeration



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WDF_IO_TARGET_STATE</b> enumeration specifies the states that an I/O target can be in.</p>


## -syntax

````
typedef enum _WDF_IO_TARGET_STATE { 
  WdfIoTargetStateUndefined        = 0,
  WdfIoTargetStarted               = 1,
  WdfIoTargetStopped               = 2,
  WdfIoTargetClosedForQueryRemove  = 3,
  WdfIoTargetClosed                = 4,
  WdfIoTargetDeleted               = 5,
  WdfIoTargetPurged                = 6
} WDF_IO_TARGET_STATE, *PWDF_IO_TARGET_STATE;
````


## -enum-fields
<dl>

### -field <a id="WdfIoTargetStateUndefined"></a><a id="wdfiotargetstateundefined"></a><a id="WDFIOTARGETSTATEUNDEFINED"></a><b>WdfIoTargetStateUndefined</b>

<dd>
<p>Reserved for internal use.</p>
</dd>

### -field <a id="WdfIoTargetStarted"></a><a id="wdfiotargetstarted"></a><a id="WDFIOTARGETSTARTED"></a><b>WdfIoTargetStarted</b>

<dd>
<p>The I/O target is started and can process I/O requests.</p>
</dd>

### -field <a id="WdfIoTargetStopped"></a><a id="wdfiotargetstopped"></a><a id="WDFIOTARGETSTOPPED"></a><b>WdfIoTargetStopped</b>

<dd>
<p>The I/O target is temporarily stopped and cannot process I/O requests.</p>
</dd>

### -field <a id="WdfIoTargetClosedForQueryRemove"></a><a id="wdfiotargetclosedforqueryremove"></a><a id="WDFIOTARGETCLOSEDFORQUERYREMOVE"></a><b>WdfIoTargetClosedForQueryRemove</b>

<dd>
<p>The I/O target's underlying device might be removed in the near future.</p>
</dd>

### -field <a id="WdfIoTargetClosed"></a><a id="wdfiotargetclosed"></a><a id="WDFIOTARGETCLOSED"></a><b>WdfIoTargetClosed</b>

<dd>
<p>The I/O target is permanently stopped and cannot process I/O requests. </p>
</dd>

### -field <a id="WdfIoTargetDeleted"></a><a id="wdfiotargetdeleted"></a><a id="WDFIOTARGETDELETED"></a><b>WdfIoTargetDeleted</b>

<dd>
<p>The I/O target's underlying device has been removed.</p>
</dd>

### -field <a id="WdfIoTargetPurged"></a><a id="wdfiotargetpurged"></a><a id="WDFIOTARGETPURGED"></a><b>WdfIoTargetPurged</b>

<dd>
<p>The I/O target is temporarily purged and cannot receive or process I/O requests. This constant is available starting in KMDF 1.11.</p>
</dd>
</dl>

## -remarks
<p>To obtain an I/O target's current state, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548631">WdfIoTargetGetState</a>.</p>

<p>For more information about states for I/O targets, see <a href="wdf.controlling_a_general_i_o_target_s_state">Controlling a General I/O Target's State</a>.</p>

<p>To obtain an I/O target's current state, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548631">WdfIoTargetGetState</a>.</p>

<p>For more information about states for I/O targets, see <a href="wdf.controlling_a_general_i_o_target_s_state">Controlling a General I/O Target's State</a>.</p>

<p>To obtain an I/O target's current state, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548631">WdfIoTargetGetState</a>.</p>

<p>For more information about states for I/O targets, see <a href="wdf.controlling_a_general_i_o_target_s_state">Controlling a General I/O Target's State</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.11</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfiotarget.h (include Wdf.h); </dt>
<dt>Wudfddi_types.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548631">WdfIoTargetGetState</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_IO_TARGET_STATE enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
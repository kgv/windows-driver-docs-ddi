---
UID: NF.scsiwmi.ScsiPortWmiDispatchFunction
title: ScsiPortWmiDispatchFunction
author: windows-driver-content
description: The ScsiPortWmiDispatchFunction routine is a dispatch routine for miniport drivers that support WMI.
old-location: storage\scsiportwmidispatchfunction.htm
ms.assetid: 48806050-403b-4375-8b19-e867f905b761
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: scsiwmi.h
req.include-header: Miniport.h, Scsi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ScsiPortWmiDispatchFunction
req.alt-loc: scsiwmi.h
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
ms.keywords: ScsiPortWmiDispatchFunction
req.iface: 
req.product: Windows 10 or later.
---

# ScsiPortWmiDispatchFunction function



## -description
<p>The <b>ScsiPortWmiDispatchFunction</b> routine is a dispatch routine for miniport drivers that support WMI. </p>


## -syntax

````
BOOLEAN ScsiPortWmiDispatchFunction(
  _In_ PSCSI_WMILIB_CONTEXT     WmiLibInfo,
  _In_ UCHAR                    MinorFunction,
  _In_ PVOID                    DeviceContext,
  _In_ PSCSIWMI_REQUEST_CONTEXT RequestContext,
  _In_ PVOID                    DataPath,
  _In_ ULONG                    BufferSize,
  _In_ PVOID                    Buffer
);
````


## -parameters
<dl>

### -param <i>WmiLibInfo</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff565395">SCSI_WMILIB_CONTEXT</a> structure that contains registration information for a miniport driver's data blocks and event blocks and defines entry points for the miniport driver's WMI library callback routines.</p>
</dd>

### -param <i>MinorFunction</i> [in]

<dd>
<p>Indicates the WMI action to perform. The miniport driver sets <i>MinorFunction</i> to <b>Srb-&gt;WmiSubFunction</b> from the input SRB.</p>
</dd>

### -param <i>DeviceContext</i> [in]

<dd>
<p>Pointer to a miniport driver-defined context value. The port driver will pass <i>DeviceContext</i> to the miniport driver's <i>HwScsiWmiXxx</i> callback routine. This value would typically point to a HW_DEVICE_EXTENSION structure.</p>
</dd>

### -param <i>RequestContext</i> [in]

<dd>
<p>Pointer to a SCSIWMI_REQUEST_CONTEXT structure that contains context information for the WMI SRB. If the SRB can pend, the miniport driver must allocate this structure from the SRB extension because the request context must remain valid until after <b>ScsiPortWmiPostProcess</b> returns with the final SRB return status and buffer size. <b>ScsiPortWmiDispatchFunction </b>will pass <i>RequestContext</i> to the miniport driver's callback routine that processes this request.</p>
</dd>

### -param <i>DataPath</i> [in]

<dd>
<p>Pointer to a GUID that represents the data block associated with the request. The miniport driver sets <i>DataPath</i> to <b>Srb-&gt;DataPath</b> from the input SRB.</p>
</dd>

### -param <i>BufferSize</i> [in]

<dd>
<p>Specifies the size in bytes of the data buffer. The miniport driver sets <i>BufferSize</i> to <b>Srb-&gt;DataTransferLength</b> from the input SRB.</p>
</dd>

### -param <i>Buffer</i> [in]

<dd>
<p>Pointer to the data buffer. The miniport driver sets <i>Buffer</i> to <b>Srb-&gt;DataBuffer</b> from the input SRB.</p>
</dd>
</dl>

## -returns
<p><b>ScsiPortWmiDispatchFunction</b> returns <b>TRUE</b> if the request is pending, or <b>FALSE</b> if the request was completed.</p>

## -remarks
<p>When a miniport driver receives an SRB in which the <b>Function</b> member is set to SRB_FUNCTION_WMI, it calls <b>ScsiPortWmiDispatchFunction</b> with request parameters, including a pointer to an initialized SCSI_WMILIB_CONTEXT structure. This structure contains information about the miniport driver's data blocks and event blocks and defines entry points for the miniport driver's <i>HwScsiWmiXxx</i> callback routines. </p>

<p><b>ScsiPortWmiDispatchFunction</b> confirms that the SRB is a WMI request and determines whether the block specified by the request is valid for the miniport driver. If these conditions are met, <b>ScsiPortWmiDispatchFunction</b> processes the SRB by calling the appropriate <i>HwScsiWmiXxx</i> entry point in the miniport driver's SCSI_WMILIB_CONTEXT structure. If the miniport driver does not define an entry point for an optional <i>HwScsiWmiXxx</i> routine, the port driver handles the request.</p>

<p>In either case, after <b>ScsiPortWmiDispatchFunction</b> returns, the miniport driver should do the following for requests that it does not pend:</p>

<p>Set <b>Srb-&gt;DataTransferLength</b> to the value returned by <b>ScsiPortWmiGetReturnSize</b></p>

<p>Set <b>Srb-&gt;SrbStatus</b> to the value returned by <b>ScsiPortWmiGetReturnStatus</b></p>

<p>Call <b>ScsiPortNotification</b> with <b>RequestComplete</b> and again with <b>NextRequest</b></p>

<p>When a miniport driver receives an SRB in which the <b>Function</b> member is set to SRB_FUNCTION_WMI, it calls <b>ScsiPortWmiDispatchFunction</b> with request parameters, including a pointer to an initialized SCSI_WMILIB_CONTEXT structure. This structure contains information about the miniport driver's data blocks and event blocks and defines entry points for the miniport driver's <i>HwScsiWmiXxx</i> callback routines. </p>

<p><b>ScsiPortWmiDispatchFunction</b> confirms that the SRB is a WMI request and determines whether the block specified by the request is valid for the miniport driver. If these conditions are met, <b>ScsiPortWmiDispatchFunction</b> processes the SRB by calling the appropriate <i>HwScsiWmiXxx</i> entry point in the miniport driver's SCSI_WMILIB_CONTEXT structure. If the miniport driver does not define an entry point for an optional <i>HwScsiWmiXxx</i> routine, the port driver handles the request.</p>

<p>In either case, after <b>ScsiPortWmiDispatchFunction</b> returns, the miniport driver should do the following for requests that it does not pend:</p>

<p>Set <b>Srb-&gt;DataTransferLength</b> to the value returned by <b>ScsiPortWmiGetReturnSize</b></p>

<p>Set <b>Srb-&gt;SrbStatus</b> to the value returned by <b>ScsiPortWmiGetReturnStatus</b></p>

<p>Call <b>ScsiPortNotification</b> with <b>RequestComplete</b> and again with <b>NextRequest</b></p>

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
<dt>Scsiwmi.h (include Miniport.h or Scsi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565395">SCSI_WMILIB_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564657">ScsiPortNotification</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564789">ScsiPortWmiGetReturnSize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564791">ScsiPortWmiGetReturnStatus</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564796">ScsiPortWmiPostProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564946">SCSIWMI_REQUEST_CONTEXT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ScsiPortWmiDispatchFunction routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
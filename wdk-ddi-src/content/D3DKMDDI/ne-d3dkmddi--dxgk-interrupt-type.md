---
UID: NE.d3dkmddi._DXGK_INTERRUPT_TYPE
title: DXGK_INTERRUPT_TYPE
author: windows-driver-content
description: The DXGK_INTERRUPT_TYPE enumeration indicates the type of interrupt that the display miniport driver notifies the graphics processing unit (GPU) scheduler about.
old-location: display\dxgk_interrupt_type.htm
ms.assetid: f942e448-94b8-400b-927b-fb5f2b1f544e
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_INTERRUPT_TYPE
req.alt-loc: d3dkmddi.h
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
ms.keywords: DD_MULTISAMPLEQUALITYLEVELSDATA, DD_MULTISAMPLEQUALITYLEVELSDATA
req.iface: 
---

# DXGK_INTERRUPT_TYPE enumeration



## -description
<p>The DXGK_INTERRUPT_TYPE enumeration indicates the type of interrupt that the display miniport driver notifies the graphics processing unit (GPU) scheduler about.</p>


## -syntax

````
typedef enum _DXGK_INTERRUPT_TYPE { 
  DXGK_INTERRUPT_DMA_COMPLETED                       = 1,
  DXGK_INTERRUPT_DMA_PREEMPTED                       = 2,
  DXGK_INTERRUPT_CRTC_VSYNC                          = 3,
  DXGK_INTERRUPT_DMA_FAULTED                         = 4,
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WIN8)
  DXGK_INTERRUPT_DISPLAYONLY_VSYNC                   = 5,
  DXGK_INTERRUPT_DISPLAYONLY_PRESENT_PROGRESS        = 6,
  DXGK_INTERRUPT_CRTC_VSYNC_WITH_MULTIPLANE_OVERLAY  = 7,
#endif 
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM1_3_M1)
  DXGK_INTERRUPT_MICACAST_ENCODE_CHUNK_COMPLETE      = 8,
#endif 
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM2_0)
  DXGK_INTERRUPT_DMA_PAGE_FAULTED                    = 9,
#endif 
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM2_2)
  DXGK_INTERRUPT_PERIODIC_MONITORED_FENCE_SIGNALED   = 11
} DXGK_INTERRUPT_TYPE;
````


## -enum-fields
<dl>

### -field <a id="DXGK_INTERRUPT_DMA_COMPLETED"></a><a id="dxgk_interrupt_dma_completed"></a><b>DXGK_INTERRUPT_DMA_COMPLETED</b>

<dd>
<p>A direct memory access (DMA) buffer is completed by using a fence identifier. The driver must supply the DMA buffer fence identifier in the <b>SubmissionFenceId</b> member of the <b>DmaCompleted</b> structure in the union that is contained in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557538">DXGKARGCB_NOTIFY_INTERRUPT_DATA</a> structure in a call to the <a href="https://msdn.microsoft.com/7968d26d-0195-463d-8954-e7ebef4f9dea">DxgkCbNotifyInterrupt</a> function. This DMA buffer fence identifier was assigned during a call to the driver's <a href="https://msdn.microsoft.com/de1925ab-e444-4cf6-acd9-8fdab26afcec">DxgkDdiSubmitCommand</a> function for the latest completed DMA buffer.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_DMA_PREEMPTED"></a><a id="dxgk_interrupt_dma_preempted"></a><b>DXGK_INTERRUPT_DMA_PREEMPTED</b>

<dd>
<p>A preemption request is completed. The driver must supply the preemption fence identifier in the <b>PreemptionFenceId</b> member and the latest fence identifier that hardware completed (not preempted) in the <b>LastCompletedFenceId</b> member of the <b>DmaPreempted</b> structure in the union that is contained in the DXGKARGCB_NOTIFY_INTERRUPT_DATA structure in a call to the <a href="https://msdn.microsoft.com/7968d26d-0195-463d-8954-e7ebef4f9dea">DxgkCbNotifyInterrupt</a> function.</p>
<p>The GPU scheduler determines that the graphics hardware preempted all of the commands between the preemption request and the submission with the latest fence identifier. </p>
</dd>

### -field <a id="DXGK_INTERRUPT_CRTC_VSYNC"></a><a id="dxgk_interrupt_crtc_vsync"></a><b>DXGK_INTERRUPT_CRTC_VSYNC</b>

<dd>
<p>A scan out is completed. The driver must supply information in the <b>CrtcVsync</b> structure in the union that is contained in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557538">DXGKARGCB_NOTIFY_INTERRUPT_DATA</a> structure in a call to the <a href="https://msdn.microsoft.com/7968d26d-0195-463d-8954-e7ebef4f9dea">DxgkCbNotifyInterrupt</a> function. </p>
<p>The display miniport driver notifies with this interrupt type after video hardware entered into the vertical retrace period, and the pending flip address was latched into the DAC and scanned out. The display miniport driver is not required to report this interrupt after the operating system calls the driver's <a href="https://msdn.microsoft.com/d6bef242-bafc-4d9e-a729-d62ccdbd2667">DxgkDdiControlInterrupt</a> function to disable the interrupt type; however, the driver must resume reporting after the operating system calls the driver's <i>DxgkDdiControlInterrupt</i> function again to enable the interrupt type. </p>
</dd>

### -field <a id="DXGK_INTERRUPT_DMA_FAULTED"></a><a id="dxgk_interrupt_dma_faulted"></a><b>DXGK_INTERRUPT_DMA_FAULTED</b>

<dd>
<p>Reserved for system use. Do not use in your driver.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_DISPLAYONLY_VSYNC"></a><a id="dxgk_interrupt_displayonly_vsync"></a><b>DXGK_INTERRUPT_DISPLAYONLY_VSYNC</b>

<dd>
<p>In a kernel mode display-only driver, a VSync has completed.</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_DISPLAYONLY_PRESENT_PROGRESS"></a><a id="dxgk_interrupt_displayonly_present_progress"></a><b>DXGK_INTERRUPT_DISPLAYONLY_PRESENT_PROGRESS</b>

<dd>
<p>In a kernel mode display-only driver, a present operation has completed or has failed.</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_CRTC_VSYNC_WITH_MULTIPLANE_OVERLAY"></a><a id="dxgk_interrupt_crtc_vsync_with_multiplane_overlay"></a><b>DXGK_INTERRUPT_CRTC_VSYNC_WITH_MULTIPLANE_OVERLAY</b>

<dd>
<p>A Vsync has completed in a display miniport driver that supports multiplane overlays.</p>
<p>Supported starting with Windows 8.1.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_MICACAST_ENCODE_CHUNK_COMPLETE"></a><a id="dxgk_interrupt_micacast_encode_chunk_complete"></a><b>DXGK_INTERRUPT_MICACAST_ENCODE_CHUNK_COMPLETE</b>

<dd>
<p>The GPU has completed encoding a Miracast encode chunk.</p>
<p>The display miniport driver can optionally provide private data that the user-mode driver can obtain using the <a href="https://msdn.microsoft.com/24b1d89a-4200-41ec-aa73-15b37e4cca6d">GetNextChunkData</a>  function.</p>
<p>Supported starting with Windows 8.1.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_DMA_PAGE_FAULTED"></a><a id="dxgk_interrupt_dma_page_faulted"></a><b>DXGK_INTERRUPT_DMA_PAGE_FAULTED</b>

<dd>
<p>This interrupt type should be raised when a GPU encounters an error condition that requires OS to perform a recovery action, such as putting the running packet device in error or resetting the GPU.
</p>
<p>When this interrupt type is set, interrupt data should be provided in the <b>DmaPageFaulted</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff557538">DXGKARGCB_NOTIFY_INTERRUPT_DATA</a> structure.</p>
<p>Supported starting with Windows 10.</p>
</dd>

### -field <a id="DXGK_INTERRUPT_PERIODIC_MONITORED_FENCE_SIGNALED"></a><a id="dxgk_interrupt_periodic_monitored_fence_signaled"></a><b>DXGK_INTERRUPT_PERIODIC_MONITORED_FENCE_SIGNALED</b>

<dd>
<p>This interrupt type should be raised when the periodic monitored fence is signaled. </p>
<p>Supported starting with Windows 10.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557538">DXGKARGCB_NOTIFY_INTERRUPT_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7968d26d-0195-463d-8954-e7ebef4f9dea">DxgkCbNotifyInterrupt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d6bef242-bafc-4d9e-a729-d62ccdbd2667">DxgkDdiControlInterrupt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/de1925ab-e444-4cf6-acd9-8fdab26afcec">DxgkDdiSubmitCommand</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/24b1d89a-4200-41ec-aa73-15b37e4cca6d">GetNextChunkData</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGK_INTERRUPT_TYPE enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
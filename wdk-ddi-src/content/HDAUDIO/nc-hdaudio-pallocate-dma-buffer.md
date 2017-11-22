---
UID: NC.hdaudio.PALLOCATE_DMA_BUFFER
title: PALLOCATE_DMA_BUFFER
author: windows-driver-content
description: The AllocateDmaBuffer routine allocates a data buffer in system memory for a DMA engine.The function pointer type for an AllocateDmaBuffer routine is defined as:
old-location: audio\allocatedmabuffer.htm
ms.assetid: 44fd988a-24b3-4587-88d9-30585800ffbf
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: audio
req.header: hdaudio.h
req.include-header: Hdaudio.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: AllocateDmaBuffer
req.alt-loc: hdaudio.h
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
ms.keywords: SM_SetRNIDMgmtInfo_OUT, SM_SetRNIDMgmtInfo_OUT, *PSM_SetRNIDMgmtInfo_OUT
req.iface: 
---

# PALLOCATE_DMA_BUFFER callback



## -description
<p>The <code>AllocateDmaBuffer</code> routine allocates a data buffer in system memory for a DMA engine.</p>
<p>The function pointer type for an <code>AllocateDmaBuffer</code> routine is defined as:</p>


## -prototype

````
PALLOCATE_DMA_BUFFER AllocateDmaBuffer;

NTSTATUS AllocateDmaBuffer(
  _In_  PVOID   context,
  _In_  HANDLE  handle,
  _In_  SIZE_T  requestedBufferSize,
  _Out_ PMDL    *bufferMdl,
  _Out_ PSIZE_T allocatedBufferSize,
  _Out_ PUCHAR  streamID,
  _Out_ PULONG  fifoSize
)
{ ... }
````


## -parameters
<dl>

### -param <i>context</i> [in]

<dd>
<p>Specifies the context value from the <b>Context</b> members of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536413">HDAUDIO_BUS_INTERFACE</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff536418">HDAUDIO_BUS_INTERFACE_V2</a> structures.</p>
</dd>

### -param <i>handle</i> [in]

<dd>
<p>Handle identifying the DMA engine. This handle value was obtained from a previous call to <a href="https://msdn.microsoft.com/038e52be-04db-41c2-aa19-85bc4eb8bc57">AllocateCaptureDmaEngine</a> or <a href="https://msdn.microsoft.com/fb2a64ca-7e8e-4352-86c6-b9500e535c75">AllocateRenderDmaEngine</a>.</p>
</dd>

### -param <i>requestedBufferSize</i> [in]

<dd>
<p>Specifies the requested buffer size in bytes.</p>
</dd>

### -param <i>bufferMdl</i> [out]

<dd>
<p>Retrieves the physical memory pages that contains the allocated buffer. This parameter points to a caller-allocated PMDL variable into which the routine writes a pointer to a memory descriptor list (MDL) that describes the buffer.</p>
</dd>

### -param <i>allocatedBufferSize</i> [out]

<dd>
<p>Retrieves the allocated buffer size in bytes. This parameter points to a caller-allocated SIZE_T variable into which the routine writes the size of the allocated buffer.</p>
</dd>

### -param <i>streamID</i> [out]

<dd>
<p>Retrieves the stream identifier. This parameter points to a caller-allocated UCHAR variable into which the routine writes the stream identifier that it assigns to the stream.</p>
</dd>

### -param <i>fifoSize</i> [out]

<dd>
<p>Retrieves the DMA engine's FIFO size in bytes. This parameter points to a caller-allocated ULONG variable into which the routine writes the FIFO size.</p>
</dd>
</dl>

## -returns
<p><code>AllocateDmaBuffer</code> returns STATUS_SUCCESS if the call succeeds. Otherwise, the routine returns an appropriate error code. The following table shows some of the possible return status codes.</p><dl>
<dt><b>STATUS_UNSUCCESSFUL</b></dt>
</dl><p>Indicates that the caller is running at an IRQL that is too high.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>Indicates that buffer allocation failed.</p><dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><p>Indicates that the handle parameter value is invalid.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>Indicates that one of the parameter values is incorrect (bad pointer).</p><dl>
<dt><b>STATUS_DEVICE_NOT_READY</b></dt>
</dl><p>Indicates that the hardware programming timed out. If this occurs, the hardware might be in a compromised state.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>Indicates that the stream is not in the reset state or that a buffer is already allocated for the DMA engine.</p>

<p> </p>

## -remarks
<p>The <code>AllocateDmaBuffer</code> routine is used in conjunction with the <a href="https://msdn.microsoft.com/658e32d2-40e2-4479-8212-df7140fe6b74">FreeDmaBuffer</a> routine. These two routines are available only in the HDAUDIO_BUS_INTERFACE and the HDAUDIO_BUS_INTERFACE_V2 versions of the HD Audio DDI. This DDI does not include the <a href="https://msdn.microsoft.com/4538ce8e-fccd-4862-b226-a99fe578a5fd">AllocateContiguousDmaBuffer</a>, <a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>, and <a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a> routines, which are never used in conjunction with <code>AllocateDmaBuffer</code> and <b>FreeDmaBuffer</b>. Unlike <b>SetupDmaEngineWithBdl</b>, which configures the DMA engine to use a previously allocated DMA buffer, <code>AllocateDmaBuffer</code> both allocates a DMA buffer and configures the DMA engine to use the buffer.</p>

<p>If the DMA engine cannot use a buffer of the size requested in parameter <i>requestedBufferSize</i>, the routine allocates a buffer that is as close as possible to the requested size.</p>

<p>The function driver for an audio or modem codec is responsible for programming the codec to manage the data transfers and to recognize the stream identifier.</p>

<p>The routine outputs an MDL that lists the physical memory pages that contain the buffer. The buffer base address coincides with the start of the first physical page in the list.</p>

<p>During the lifetime of a DMA engine handle, <code>AllocateDmaBuffer</code> can be called successively to allocate new DMA buffers. However, before calling <code>AllocateDmaBuffer</code>, any previously allocated DMA buffer must first be freed by calling <b>FreeDmaBuffer</b>.</p>

<p>During calls to <code>AllocateDmaBuffer</code> and <b>FreeDmaBuffer</b>, the DMA engine must be in the reset stream state. The DMA engine is in the reset state immediately following the call to Allocate<i>Xxx</i>DmaEngine. To change the DMA engine to the run state, call <a href="https://msdn.microsoft.com/05cfb827-e143-4d77-b378-e02dd381e429">SetDmaEngineState</a>.</p>

<p>The FIFO size is the maximum number of bytes that the DMA engine can hold in its internal buffer. Depending on the hardware implementation, a DMA engine's FIFO size can either be static or vary dynamically with changes in the stream format. For more information about the FIFO size, see the Intel High Definition Audio Specification at the <a href="http://go.microsoft.com/fwlink/p/?linkid=42508">Intel HD Audio</a> website.</p>

<p>This routine fails and returns error code STATUS_INVALID_DEVICE_REQUEST in either of the following circumstances:</p>

<p>Any previously allocated DMA buffer has not been freed (by calling <b>FreeDmaBuffer</b>).</p>

<p>The stream is in a state other than reset.</p>

<p>In Windows Server 2003, Windows XP, Windows 2000, and Windows Me/98, a WDM audio driver calls this routine during execution of its <b>NewStream</b> method (at pin-creation time) or <b>SetFormat</b> method (after calling one of the Allocate<i>Xxx</i>DmaEngine routines in the HD Audio DDI). For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff536735">IMiniportWavePci::NewStream</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff536732">IMiniportWavePciStream::SetFormat</a>.</p>

<p>The <code>AllocateDmaBuffer</code> routine is used in conjunction with the <a href="https://msdn.microsoft.com/658e32d2-40e2-4479-8212-df7140fe6b74">FreeDmaBuffer</a> routine. These two routines are available only in the HDAUDIO_BUS_INTERFACE and the HDAUDIO_BUS_INTERFACE_V2 versions of the HD Audio DDI. This DDI does not include the <a href="https://msdn.microsoft.com/4538ce8e-fccd-4862-b226-a99fe578a5fd">AllocateContiguousDmaBuffer</a>, <a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>, and <a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a> routines, which are never used in conjunction with <code>AllocateDmaBuffer</code> and <b>FreeDmaBuffer</b>. Unlike <b>SetupDmaEngineWithBdl</b>, which configures the DMA engine to use a previously allocated DMA buffer, <code>AllocateDmaBuffer</code> both allocates a DMA buffer and configures the DMA engine to use the buffer.</p>

<p>If the DMA engine cannot use a buffer of the size requested in parameter <i>requestedBufferSize</i>, the routine allocates a buffer that is as close as possible to the requested size.</p>

<p>The function driver for an audio or modem codec is responsible for programming the codec to manage the data transfers and to recognize the stream identifier.</p>

<p>The routine outputs an MDL that lists the physical memory pages that contain the buffer. The buffer base address coincides with the start of the first physical page in the list.</p>

<p>During the lifetime of a DMA engine handle, <code>AllocateDmaBuffer</code> can be called successively to allocate new DMA buffers. However, before calling <code>AllocateDmaBuffer</code>, any previously allocated DMA buffer must first be freed by calling <b>FreeDmaBuffer</b>.</p>

<p>During calls to <code>AllocateDmaBuffer</code> and <b>FreeDmaBuffer</b>, the DMA engine must be in the reset stream state. The DMA engine is in the reset state immediately following the call to Allocate<i>Xxx</i>DmaEngine. To change the DMA engine to the run state, call <a href="https://msdn.microsoft.com/05cfb827-e143-4d77-b378-e02dd381e429">SetDmaEngineState</a>.</p>

<p>The FIFO size is the maximum number of bytes that the DMA engine can hold in its internal buffer. Depending on the hardware implementation, a DMA engine's FIFO size can either be static or vary dynamically with changes in the stream format. For more information about the FIFO size, see the Intel High Definition Audio Specification at the <a href="http://go.microsoft.com/fwlink/p/?linkid=42508">Intel HD Audio</a> website.</p>

<p>This routine fails and returns error code STATUS_INVALID_DEVICE_REQUEST in either of the following circumstances:</p>

<p>Any previously allocated DMA buffer has not been freed (by calling <b>FreeDmaBuffer</b>).</p>

<p>The stream is in a state other than reset.</p>

<p>In Windows Server 2003, Windows XP, Windows 2000, and Windows Me/98, a WDM audio driver calls this routine during execution of its <b>NewStream</b> method (at pin-creation time) or <b>SetFormat</b> method (after calling one of the Allocate<i>Xxx</i>DmaEngine routines in the HD Audio DDI). For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff536735">IMiniportWavePci::NewStream</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff536732">IMiniportWavePciStream::SetFormat</a>.</p>

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
<dt>Hdaudio.h (include Hdaudio.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536413">HDAUDIO_BUS_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536418">HDAUDIO_BUS_INTERFACE_V2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/038e52be-04db-41c2-aa19-85bc4eb8bc57">AllocateCaptureDmaEngine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/fb2a64ca-7e8e-4352-86c6-b9500e535c75">AllocateRenderDmaEngine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/658e32d2-40e2-4479-8212-df7140fe6b74">FreeDmaBuffer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3f068ac0-2b18-4242-86de-7044ce558788">FreeDmaEngine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/05cfb827-e143-4d77-b378-e02dd381e429">SetDmaEngineState</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536735">IMiniportWavePci::NewStream</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536732">IMiniportWavePciStream::SetFormat</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PALLOCATE_DMA_BUFFER callback function%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
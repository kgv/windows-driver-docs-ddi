---
UID: NS.d3d10umddi.D3D11_1DDI_VIDEO_PROCESSOR_CAPS
title: D3D11_1DDI_VIDEO_PROCESSOR_CAPS
author: windows-driver-content
description: Describes the capabilities of a Microsoft Direct3D 11 video processor.
old-location: display\d3d11_1ddi_video_processor_caps.htm
ms.assetid: d825a0d1-fa58-4525-bf90-eb7eaee0cfba
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_1DDI_VIDEO_PROCESSOR_CAPS
req.alt-loc: D3d10umddi.h
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
ms.keywords: D3D11_1DDI_VIDEO_PROCESSOR_CAPS, D3D11_1DDI_VIDEO_PROCESSOR_CAPS
req.iface: 
---

# D3D11_1DDI_VIDEO_PROCESSOR_CAPS structure



## -description
<p>Describes the capabilities of a Microsoft Direct3D 11 video processor.</p>


## -syntax

````
typedef struct D3D11_1DDI_VIDEO_PROCESSOR_CAPS {
  UINT DeviceCaps;
  UINT FeatureCaps;
  UINT FilterCaps;
  UINT InputFormatCaps;
  UINT AutoStreamCaps;
  UINT StereoCaps;
  UINT RateConversionCapsCount;
  UINT MaxInputStreams;
  UINT MaxStreamStates;
} D3D11_1DDI_VIDEO_PROCESSOR_CAPS;
````


## -struct-fields
<dl>

### -field <b>DeviceCaps</b>

<dd>
<p>A bitwise <b>OR</b> of zero or more flags from the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450978">D3D11_1DDI_VIDEO_PROCESSOR_DEVICE_CAPS</a> enumeration.</p>
</dd>

### -field <b>FeatureCaps</b>

<dd>
<p>A bitwise <b>OR</b> of zero or more flags from the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450980">D3D11_1DDI_VIDEO_PROCESSOR_FEATURE_CAPS</a> enumeration.</p>
</dd>

### -field <b>FilterCaps</b>

<dd>
<p>A bitwise <b>OR</b> of zero or more flags from the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450983">D3D11_1DDI_VIDEO_PROCESSOR_FILTER_CAPS</a> enumeration.</p>
</dd>

### -field <b>InputFormatCaps</b>

<dd>
<p>A bitwise <b>OR</b> of zero or more flags from the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450986">D3D11_1DDI_VIDEO_PROCESSOR_FORMAT_CAPS</a> enumeration.</p>
</dd>

### -field <b>AutoStreamCaps</b>

<dd>
<p>A bitwise <b>OR</b> of zero or more flags from the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450966">D3D11_1DDI_VIDEO_PROCESSOR_AUTO_STREAM_CAPS</a> enumeration.</p>
</dd>

### -field <b>StereoCaps</b>

<dd>
<p>A bitwise <b>OR</b> of zero or more flags from the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451023">D3D11_1DDI_VIDEO_PROCESSOR_STEREO_CAPS</a> enumeration.</p>
</dd>

### -field <b>RateConversionCapsCount</b>

<dd>
<p>The number of frame-rate conversion capabilities. To enumerate the frame-rate conversion capabilities, call the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451690">GetVideoProcessorRateConversionCaps</a> function.</p>
</dd>

### -field <b>MaxInputStreams</b>

<dd>
<p>The maximum number of input streams that can be enabled at the same time.</p>
</dd>

### -field <b>MaxStreamStates</b>

<dd>
<p>The maximum number of input streams for which the device can store state data.</p>
</dd>
</dl>

## -remarks
<p>The video processor stores state information for each input stream. These states persist between blits. With each blit, the application selects which streams to enable or disable. Disabling a stream does not affect the state information for that stream.</p>

<p>The <b>MaxStreamStates</b> member gives the maximum number of stream states that can be saved. The <b>MaxInputStreams</b> member gives the maximum number of streams that can be enabled during a blit. These two values can differ.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh450966">D3D11_1DDI_VIDEO_PROCESSOR_AUTO_STREAM_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh450978">D3D11_1DDI_VIDEO_PROCESSOR_DEVICE_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh450980">D3D11_1DDI_VIDEO_PROCESSOR_FEATURE_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh450983">D3D11_1DDI_VIDEO_PROCESSOR_FILTER_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh450986">D3D11_1DDI_VIDEO_PROCESSOR_FORMAT_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451023">D3D11_1DDI_VIDEO_PROCESSOR_STEREO_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451690">GetVideoProcessorRateConversionCaps</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D11_1DDI_VIDEO_PROCESSOR_CAPS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
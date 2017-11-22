---
UID: NC.video.PVIDEO_READ_DATA_LINE
title: PVIDEO_READ_DATA_LINE
author: windows-driver-content
description: ReadDataLine reads a single data bit from the I2C serial data line.
old-location: display\readdataline.htm
ms.assetid: 071000a3-c1b7-47fd-aec7-9e9f32edddf6
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ReadDataLine
req.alt-loc: video.h
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
ms.keywords: VHF_CONFIG, VHF_CONFIG, *PVHF_CONFIG
req.iface: 
req.product: Windows 10 or later.
---

# PVIDEO_READ_DATA_LINE callback



## -description
<p><i>ReadDataLine</i> reads a single data bit from the I2C serial data line.</p>


## -prototype

````
PVIDEO_READ_DATA_LINE ReadDataLine;

BOOLEAN ReadDataLine(
   PVOID HwDeviceExtension
)
{ ... }
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> 

<dd>
<p>Pointer to the miniport driver's per-adapter storage area. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff543119">Device Extensions</a>.</p>
</dd>
</dl>

## -returns
<p><i>ReadDataLine</i> returns 1 if the serial data line is high and 0 if the serial data line is low.</p>

## -remarks
<p><i>ReadDataLine</i> should be made pageable.</p>

<p><i>ReadDataLine</i> should be made pageable.</p>

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
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567383">I2C Functions</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/175030c1-95d9-4a3b-976c-16e04852cb91">HwVidGetVideoChildDescriptor</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1051a234-ef63-454e-8957-292e86f4efcd">ReadClockLine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570290">VideoPortDDCMonitorHelper</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/4dfd6223-420e-4087-b5bd-8277575321f7">WriteClockLine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3f860619-a479-4291-b3f3-ea4d309beee7">WriteDataLine</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PVIDEO_READ_DATA_LINE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
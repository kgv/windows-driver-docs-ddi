---
UID: NS.d3dumddi._DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA
title: DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA
author: windows-driver-content
description: The DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA structure describes data that specifies the alpha-fill mode of the output.
old-location: display\dxvahdddi_blt_state_alpha_fill_data.htm
ms.assetid: 67fb316e-359f-4bf0-b061-a4b18e359f38
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA is supported beginning with the Windows 7 operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA
req.alt-loc: d3dumddi.h
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
ms.keywords: DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA, DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA
req.iface: 
---

# DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA structure



## -description
<p>The DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA structure describes data that specifies the alpha-fill mode of the output. </p>


## -syntax

````
typedef struct _DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA {
  DXVAHDDDI_ALPHA_FILL_MODE Mode;
  UINT                      StreamNumber;
} DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA;
````


## -struct-fields
<dl>

### -field <b>Mode</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff562974">DXVAHDDDI_ALPHA_FILL_MODE</a>-typed value that indicates the type of alpha-fill mode to set. The default value is DXVAHDDDI_ALPHA_FILL_MODE_BACKGROUND, which indicates to fill the output with the alpha value of the background color. </p>
</dd>

### -field <b>StreamNumber</b>

<dd>
<p>[in] A zero-based stream index number. This number must be less than the number, which the driver sets in the <b>MaxStreamStates</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563113">DXVAHDDDI_VPDEVCAPS</a> structure. The driver should refer to this number only when the <b>Mode</b> member is set to DXVAHD_ALPHA_FILL_MODE_SOURCE_STREAM. The default value is zero. </p>
</dd>
</dl>

## -remarks
<p>The Direct3D runtime specifies the DXVAHDDDI_BLT_STATE_ALPHA_FILL state in the <b>State</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543093">D3DDDIARG_DXVAHD_SETVIDEOPROCESSBLTSTATE</a> structure in a call to the driver's <a href="https://msdn.microsoft.com/6796372c-279d-427c-a2a4-9b7c99494f53">SetVideoProcessBltState</a> function only when the output format is a format type with alpha (for example, D3DDDIFMT_A8R8G8B8 from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544312">D3DDDIFORMAT</a> enumeration).</p>

<p>The DXVAHD_ALPHA_FILL_MODE_SOURCE_STREAM mode requires the following conditions:</p>

<p>The DXVAHDDDI_BLT_STATE_ALPHA_FILL state only affects alpha within the destination rectangle. The rest of the output remains unchanged. </p>

<p>If the input format type is without alpha, the source alpha is considered as opaque. </p>

<p>If the input stream is disabled or unavailable, the output remains unchanged. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA is supported beginning with the Windows 7 operating system.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543093">D3DDDIARG_DXVAHD_SETVIDEOPROCESSBLTSTATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544312">D3DDDIFORMAT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562974">DXVAHDDDI_ALPHA_FILL_MODE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563113">DXVAHDDDI_VPDEVCAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/6796372c-279d-427c-a2a4-9b7c99494f53">SetVideoProcessBltState</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVAHDDDI_BLT_STATE_ALPHA_FILL_DATA structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NE.d3dkmthk._D3DKMT_DEVICESTATE_TYPE
title: D3DKMT_DEVICESTATE_TYPE
author: windows-driver-content
description: The D3DKMT_DEVICESTATE_TYPE enumeration type contains values that indicate the status of a device.
old-location: display\d3dkmt_devicestate_type.htm
ms.assetid: 84570bac-63f1-4e34-919f-c150f9f0810e
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_DEVICESTATE_TYPE
req.alt-loc: d3dkmthk.h
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
ms.keywords: DXGKMDT_OPM_STANDARD_INFORMATION, DXGKMDT_OPM_STANDARD_INFORMATION
req.iface: 
---

# D3DKMT_DEVICESTATE_TYPE enumeration



## -description
<p>The D3DKMT_DEVICESTATE_TYPE enumeration type contains values that indicate the status of a device.</p>


## -syntax

````
typedef enum _D3DKMT_DEVICESTATE_TYPE { 
  D3DKMT_DEVICESTATE_EXECUTION    = 1,
  D3DKMT_DEVICESTATE_PRESENT      = 2,
  D3DKMT_DEVICESTATE_RESET        = 3,
  D3DKMT_DEVICESTATE_PRESENT_DWM  = 4,
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM2_0)
  D3DKMT_DEVICESTATE_PAGE_FAULT   = 5,
#endif 
  
} D3DKMT_DEVICESTATE_TYPE;
````


## -enum-fields
<dl>

### -field <a id="D3DKMT_DEVICESTATE_EXECUTION"></a><a id="d3dkmt_devicestate_execution"></a><b>D3DKMT_DEVICESTATE_EXECUTION</b>

<dd>
<p>The device execution state is retrieved.</p>
</dd>

### -field <a id="D3DKMT_DEVICESTATE_PRESENT"></a><a id="d3dkmt_devicestate_present"></a><b>D3DKMT_DEVICESTATE_PRESENT</b>

<dd>
<p>The device present state is retrieved.</p>
</dd>

### -field <a id="D3DKMT_DEVICESTATE_RESET"></a><a id="d3dkmt_devicestate_reset"></a><b>D3DKMT_DEVICESTATE_RESET</b>

<dd>
<p>The device reset state is retrieved.</p>
</dd>

### -field <a id="D3DKMT_DEVICESTATE_PRESENT_DWM"></a><a id="d3dkmt_devicestate_present_dwm"></a><b>D3DKMT_DEVICESTATE_PRESENT_DWM</b>

<dd>
<p>The device present desktop window manager state is retrieved.</p>
</dd>

### -field <a id="D3DKMT_DEVICESTATE_PAGE_FAULT"></a><a id="d3dkmt_devicestate_page_fault"></a><b>D3DKMT_DEVICESTATE_PAGE_FAULT</b>

<dd>
<p>The device page fault state is retrieved.</p>
</dd>

### -field <a id=""></a><b></b>

<dd></dd>
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
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548030">D3DKMT_GETDEVICESTATE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_DEVICESTATE_TYPE enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NE.d3dkmddi._DXGK_VIDPN_INTERFACE_VERSION
title: DXGK_VIDPN_INTERFACE_VERSION
author: windows-driver-content
description: The DXGK_VIDPN_INTERFACE_VERSION enumeration indicates the version of a video present network (VidPN) interface.
old-location: display\dxgk_vidpn_interface_version.htm
ms.assetid: 819261a5-bec0-49a8-942a-9313d3b793ca
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
req.alt-api: DXGK_VIDPN_INTERFACE_VERSION
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

# DXGK_VIDPN_INTERFACE_VERSION enumeration



## -description
<p>The DXGK_VIDPN_INTERFACE_VERSION enumeration indicates the version of a video present network (VidPN) interface.</p>


## -syntax

````
typedef enum _DXGK_VIDPN_INTERFACE_VERSION { 
  DXGK_VIDPN_INTERFACE_VERSION_UNINITIALIZED  = 0,
  DXGK_VIDPN_INTERFACE_VERSION_V1             = 1
} DXGK_VIDPN_INTERFACE_VERSION;
````


## -enum-fields
<dl>

### -field <a id="DXGK_VIDPN_INTERFACE_VERSION_UNINITIALIZED"></a><a id="dxgk_vidpn_interface_version_uninitialized"></a><b>DXGK_VIDPN_INTERFACE_VERSION_UNINITIALIZED</b>

<dd>
<p>Indicates that a variable of type DXGK_VIDPN_INTERFACE_VERSION has not yet been assigned a meaningful value.</p>
</dd>

### -field <a id="DXGK_VIDPN_INTERFACE_VERSION_V1"></a><a id="dxgk_vidpn_interface_version_v1"></a><b>DXGK_VIDPN_INTERFACE_VERSION_V1</b>

<dd>
<p>Indicates version 1 of the VidPN interface.</p>
</dd>
</dl>

## -remarks
<p>The <i>VidPnInterfaceVersion</i> parameter of the <a href="https://msdn.microsoft.com/649ce7fc-6852-43f3-b944-b2b64fcba874">DxgkCbQueryVidPnInterface</a> function and the <b>Version</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> structure are DXGK_VIDPN_INTERFACE_VERSION values.</p>

<p>The <i>VidPnInterfaceVersion</i> parameter of the <a href="https://msdn.microsoft.com/649ce7fc-6852-43f3-b944-b2b64fcba874">DxgkCbQueryVidPnInterface</a> function and the <b>Version</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> structure are DXGK_VIDPN_INTERFACE_VERSION values.</p>

<p>The <i>VidPnInterfaceVersion</i> parameter of the <a href="https://msdn.microsoft.com/649ce7fc-6852-43f3-b944-b2b64fcba874">DxgkCbQueryVidPnInterface</a> function and the <b>Version</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> structure are DXGK_VIDPN_INTERFACE_VERSION values.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570556">VidPn Interface</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGK_VIDPN_INTERFACE_VERSION enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
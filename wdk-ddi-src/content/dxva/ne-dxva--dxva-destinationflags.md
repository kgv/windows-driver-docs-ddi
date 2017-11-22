---
UID: NE.dxva._DXVA_DestinationFlags
title: DXVA_DestinationFlags
author: windows-driver-content
description: The DXVA_DestinationFlags enumeration type contains a collection of flags that identify changes in the current destination surface from the previous destination surface.
old-location: display\dxva_destinationflags.htm
ms.assetid: 842c6ece-5304-428c-afbe-2990d239f38a
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: dxva.h
req.include-header: Dxva.h
req.target-type: Windows
req.target-min-winverclnt: This enumeration type applies only to Windows Server 2003 with SP1 and later, and Windows XP with SP2 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXVA_DestinationFlags
req.alt-loc: dxva.h
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
ms.keywords: DXGIDDICB_PRESENT, DXGIDDICB_PRESENT
req.iface: 
---

# DXVA_DestinationFlags enumeration



## -description
<p>The DXVA_DestinationFlags enumeration type contains a collection of flags that identify changes in the current destination surface from the previous destination surface.</p>


## -syntax

````
typedef enum _DXVA_DestinationFlags { 
  DXVA_DestinationFlagMask                 = DXVABit(3)|DXVABit(2)|DXVABit(1)|DXVABit(0),
  DXVA_DestinationFlag_Background_Changed  = 0x0001,
  DXVA_DestinationFlag_TargetRect_Changed  = 0x0002,
  DXVA_DestinationFlag_ColorData_Changed   = 0x0004,
  DXVA_DestinationFlag_Alpha_Changed       = 0x0008
} DXVA_DestinationFlags;
````


## -enum-fields
<dl>

### -field <a id="DXVA_DestinationFlagMask"></a><a id="dxva_destinationflagmask"></a><a id="DXVA_DESTINATIONFLAGMASK"></a><b>DXVA_DestinationFlagMask</b>

<dd>
<p>Specifies the destination-flag mask, which consists of the first 4 bits of a DWORD.</p>
</dd>

### -field <a id="DXVA_DestinationFlag_Background_Changed"></a><a id="dxva_destinationflag_background_changed"></a><a id="DXVA_DESTINATIONFLAG_BACKGROUND_CHANGED"></a><b>DXVA_DestinationFlag_Background_Changed</b>

<dd>
<p>Indicates that the background color of the destination surface changed. </p>
</dd>

### -field <a id="DXVA_DestinationFlag_TargetRect_Changed"></a><a id="dxva_destinationflag_targetrect_changed"></a><a id="DXVA_DESTINATIONFLAG_TARGETRECT_CHANGED"></a><b>DXVA_DestinationFlag_TargetRect_Changed</b>

<dd>
<p>Indicates that the target rectangle of the destination surface changed. </p>
</dd>

### -field <a id="DXVA_DestinationFlag_ColorData_Changed"></a><a id="dxva_destinationflag_colordata_changed"></a><a id="DXVA_DESTINATIONFLAG_COLORDATA_CHANGED"></a><b>DXVA_DestinationFlag_ColorData_Changed</b>

<dd>
<p>Indicates that format information for the destination surface changed. 
</p>
</dd>

### -field <a id="DXVA_DestinationFlag_Alpha_Changed"></a><a id="dxva_destinationflag_alpha_changed"></a><a id="DXVA_DESTINATIONFLAG_ALPHA_CHANGED"></a><b>DXVA_DestinationFlag_Alpha_Changed</b>

<dd>
<p>Indicates that the planar alpha value for the destination surface changed.</p>
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
<p>This enumeration type applies only to Windows Server 2003 with SP1 and later, and Windows XP with SP2 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dxva.h (include Dxva.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/12a0e467-54f8-4cca-8ec0-aa8d04480ab6">DeinterlaceBltEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563915">DXVA_DeinterlaceBltEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVA_DestinationFlags enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
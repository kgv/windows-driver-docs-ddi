---
UID: NS.d3dkmddi._DXGK_POINTERFLAGS
title: DXGK_POINTERFLAGS
author: windows-driver-content
description: The DXGK_POINTERFLAGS structure identifies mouse pointer capabilities of the display miniport driver that the driver provides through a call to its DxgkDdiQueryAdapterInfo function.
old-location: display\dxgk_pointerflags.htm
ms.assetid: 0d49a089-700e-42c0-a1f3-7b181b8aef96
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_POINTERFLAGS
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
ms.keywords: DXGK_POINTERFLAGS, DXGK_POINTERFLAGS
req.iface: 
---

# DXGK_POINTERFLAGS structure



## -description
<p>The DXGK_POINTERFLAGS structure identifies mouse pointer capabilities of the display miniport driver that the driver provides through a call to its <a href="https://msdn.microsoft.com/f2f4c54c-7413-48e5-a165-d71f35642b6c">DxgkDdiQueryAdapterInfo</a> function.</p>


## -syntax

````
typedef struct _DXGK_POINTERFLAGS {
  union {
    struct {
      UINT Monochrome  :1;
      UINT Color  :1;
      UINT MaskedColor  :1;
      UINT Reserved  :29;
    };
    UINT Value;
  };
} DXGK_POINTERFLAGS;
````


## -struct-fields
<dl>

### -field <b>Monochrome</b>

<dd>
<p>A UINT value that specifies whether the mouse pointer can display in monochrome. Setting this member is equivalent to setting the first bit of the 32-bit <b>Value</b> member (0x00000001).</p>
</dd>

### -field <b>Color</b>

<dd>
<p>A UINT value that specifies whether the mouse pointer can display in color and with transparency (alpha). Setting this member is equivalent to setting the second bit of the 32-bit <b>Value</b> member (0x00000002).</p>
</dd>

### -field <b>MaskedColor</b>

<dd>
<p>A UINT value that specifies whether the mouse pointer can display in color and with a mask value in the transparency (alpha) bits. Setting this member is equivalent to setting the third bit of the 32-bit <b>Value</b> member (0x00000004).</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member to zero is equivalent to setting the remaining 29 bits (0xFFFFFFF8) of the 32-bit <b>Value</b> member to zeros.</p>
</dd>

### -field <b>Value</b>

<dd>
<p>A member in the union that DXGK_POINTERFLAGS contains that can hold a 32-bit value that identifies mouse pointer capabilities.</p>
</dd>
</dl>

## -remarks
<p>The display miniport driver can specify mouse pointer capabilities by setting bits in the 32-bit <b>Value</b> member or by setting individual members of the structure in the union that DXGK_POINTERFLAGS contains.</p>

<p>The driver always specifies a color mouse pointer by using a A8R8G8B8 pixel format.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561062">DXGK_DRIVERCAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557621">DXGKARG_QUERYADAPTERINFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/f2f4c54c-7413-48e5-a165-d71f35642b6c">DxgkDdiQueryAdapterInfo</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGK_POINTERFLAGS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NS.d3dumddi._D3DDDI_OVERLAYINFOFLAGS
title: D3DDDI_OVERLAYINFOFLAGS
author: windows-driver-content
description: The D3DDDI_OVERLAYINFOFLAGS structure identifies the type of overlay operation to perform.
old-location: display\d3dddi_overlayinfoflags.htm
ms.assetid: ebf31c28-857b-4885-a910-16da5a011ce1
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDI_OVERLAYINFOFLAGS
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
ms.keywords: D3DDDI_OVERLAYINFOFLAGS, D3DDDI_OVERLAYINFOFLAGS
req.iface: 
---

# D3DDDI_OVERLAYINFOFLAGS structure



## -description
<p>The D3DDDI_OVERLAYINFOFLAGS structure identifies the type of overlay operation to perform.</p>


## -syntax

````
typedef struct _D3DDDI_OVERLAYINFOFLAGS {
  union {
    struct {
      UINT DstColorKey  :1;
      UINT DstColorKeyRange  :1;
      UINT SrcColorKey  :1;
      UINT SrcColorKeyRange  :1;
      UINT Bob  :1;
      UINT Interleaved  :1;
      UINT MirrorLeftRight  :1;
      UINT MirrorUpDown  :1;
      UINT Deinterlace  :1;
      UINT LimitedRGB  :1;
      UINT YCbCrBT709  :1;
      UINT YCbCrxvYCC  :1;
      UINT Reserved  :20;
    };
    UINT   Value;
  };
} D3DDDI_OVERLAYINFOFLAGS;
````


## -struct-fields
<dl>

### -field <b>DstColorKey</b>

<dd>
<p>A UINT value that specifies whether to perform destination color keying by using the value in the <b>DstColorKeyLow</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544621">D3DDDI_OVERLAYINFO</a> structure. That is, any pixel in the destination surface that matches the color key should be replaced with the corresponding pixel from the source resource, and all of the destination pixels that do not match the color key should not be replaced. </p>
<p>Setting this member is equivalent to setting the first bit of the 32-bit <b>Value</b> member (0x00000001).</p>
</dd>

### -field <b>DstColorKeyRange</b>

<dd>
<p>A UINT value that specifies whether to perform destination color keying by using a range of values from the <b>DstColorKeyLow</b> and <b>DstColorKeyHigh</b> members of D3DDDI_OVERLAYINFO. </p>
<p>Setting this member is equivalent to setting the second bit of the 32-bit <b>Value</b> member (0x00000002).</p>
</dd>

### -field <b>SrcColorKey</b>

<dd>
<p>A UINT value that specifies whether to perform source color keying by using the value in the <b>SrcColorKeyLow</b> member of D3DDDI_OVERLAYINFO. That is, any pixel in the source resource that matches the color key should not be copied to the destination surface, and all of the source pixels that do not match the color key should be copied. </p>
<p>Setting this member is equivalent to setting the third bit of the 32-bit <b>Value</b> member (0x00000004).</p>
</dd>

### -field <b>SrcColorKeyRange</b>

<dd>
<p>A UINT value that specifies whether to perform source color keying by using a range of values from the <b>SrcColorKeyLow</b> and <b>SrcColorKeyHigh</b> members of D3DDDI_OVERLAYINFO.</p>
<p>Setting this member is equivalent to setting the fourth bit of the 32-bit <b>Value</b> member (0x00000008).</p>
</dd>

### -field <b>Bob</b>

<dd>
<p>A UINT value that specifies whether the overlay should deinterlace by using the <a href="https://msdn.microsoft.com/ef3220bd-841d-4187-bc86-11b999eae2bd">bob-style deinterlacing algorithm</a>.</p>
<p>Setting this member is equivalent to setting the fifth bit of the 32-bit <b>Value</b> member (0x00000010).</p>
</dd>

### -field <b>Interleaved</b>

<dd>
<p>A UINT value that specifies whether the allocation that is being displayed contains both even and odd fields interleaved together.</p>
<p>Setting this member is equivalent to setting the sixth bit of the 32-bit <b>Value</b> member (0x00000020).</p>
</dd>

### -field <b>MirrorLeftRight</b>

<dd>
<p>A UINT value that specifies whether the contents of the source resource are flipped horizontally along the center axis in the overlay to the destination surface. That is, contents on the left side of the source resource are copied to the right side of the destination surface, and vice versa.</p>
<p>Setting this member is equivalent to setting the seventh bit of the 32-bit <b>Value</b> member (0x00000040).</p>
</dd>

### -field <b>MirrorUpDown</b>

<dd>
<p>A UINT value that specifies whether the contents of the source resource are flipped vertically along the center axis in the overlay to the destination surface. That is, contents on the top of the source resource are copied to the bottom of the destination surface, and vice versa.</p>
<p>Setting this member is equivalent to setting the eighth bit of the 32-bit <b>Value</b> member (0x00000080).</p>
</dd>

### -field <b>Deinterlace</b>

<dd>
<p>A UINT value that specifies whether the overlay should deinterlace the data in any manner the overlay requires.</p>
<p>Setting this member is equivalent to setting the ninth bit of the 32-bit <b>Value</b> member (0x00000100).</p>
</dd>

### -field <b>LimitedRGB</b>

<dd>
<p>Supported in Windows 7 and later versions.</p>
<p>A UINT value that specifies whether the overlay is full range RGB or limited range RGB. Setting this member indicates limited range RGB. In limited range RGB, the RGB range is compressed such that 16:16:16 is black and 235:235:235 is white.</p>
<p>Setting this member is equivalent to setting the tenth bit of the 32-bit <b>Value</b> member (0x00000200).</p>
</dd>

### -field <b>YCbCrBT709</b>

<dd>
<p>Supported in Windows 7 and later versions.</p>
<p>A UINT value that specifies whether the overlay is BT.601 or BT.709. Setting this member indicates BT.709, for high-definition TV (HDTV) and</p>
<p>is equivalent to setting the eleventh bit of the 32-bit <b>Value</b> member (0x00000400).</p>
</dd>

### -field <b>YCbCrxvYCC</b>

<dd>
<p>Supported in Windows 7 and later versions.</p>
<p>A UINT value that specifies whether the overlay is conventional YCbCr or extended YCbCr (xvYCC). Setting this member indicates extended YCbCr (xvYCC) and is equivalent to setting the twelfth bit of the 32-bit <b>Value</b> member (0x00000800).</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member to zero is equivalent to setting the remaining 20 bits (0xFFFFF000) of the 32-bit <b>Value</b> member to zeros.</p>
</dd>

### -field <b>Value</b>

<dd>
<p>A member in the union that is contained in D3DDDI_OVERLAYINFOFLAGS that can hold one 32-bit value that identifies the type of overlay operation to perform.</p>
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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544621">D3DDDI_OVERLAYINFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDI_OVERLAYINFOFLAGS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
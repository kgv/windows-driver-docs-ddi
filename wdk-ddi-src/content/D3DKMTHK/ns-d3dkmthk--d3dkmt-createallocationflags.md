---
UID: NS.d3dkmthk._D3DKMT_CREATEALLOCATIONFLAGS
title: D3DKMT_CREATEALLOCATIONFLAGS
author: windows-driver-content
description: The D3DKMT_CREATEALLOCATIONFLAGS structure identifies how to create an allocation in a call to the D3DKMTCreateAllocation function.
old-location: display\d3dkmt_createallocationflags.htm
ms.assetid: ddcb8222-808b-4dfe-9303-a588b3522ebe
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_CREATEALLOCATIONFLAGS
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
ms.keywords: D3DKMT_CREATEALLOCATIONFLAGS, D3DKMT_CREATEALLOCATIONFLAGS
req.iface: 
---

# D3DKMT_CREATEALLOCATIONFLAGS structure



## -description
<p>The D3DKMT_CREATEALLOCATIONFLAGS structure identifies how to create an allocation in a call to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546807">D3DKMTCreateAllocation</a> function.</p>


## -syntax

````
typedef struct _D3DKMT_CREATEALLOCATIONFLAGS {
  UINT CreateResource  :1;
  UINT CreateShared  :1;
  UINT NonSecure  :1;
  UINT CreateProtected  :1;
  UINT RestrictSharedAccess  :1;
  UINT ExistingSysMem  :1;
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WIN8)
  UINT NtSecuritySharing  :1;
  UINT ReadOnly  :1;
  UINT CreateWriteCombined  :1;
  UINT CreateCached  :1;
  UINT SwapChainBackBuffer  :1;
  UINT Reserved  :21;
#else 
  UINT Reserved  :26;
} D3DKMT_CREATEALLOCATIONFLAGS;
````


## -struct-fields
<dl>

### -field <b>CreateResource</b>

<dd>
<p>A UINT value that specifies whether to create a device-specific resource.</p>
<p>If you set <b>CreateShared</b>, you must also set <b>CreateResource</b>.</p>
<p>Setting this member is equivalent to setting the first bit of a 32-bit value (0x00000001).</p>
</dd>

### -field <b>CreateShared</b>

<dd>
<p>A UINT value that specifies whether to create a resource shared across all devices. </p>
<p>If you set <b>CreateShared</b>, you must also set <b>CreateResource</b>.</p>
<p>For more information on using <b>CreateShared</b>, see the Remarks section.</p>
<p>Setting this member is equivalent to setting the second bit of a 32-bit value (0x00000002).</p>
</dd>

### -field <b>NonSecure</b>

<dd>
<p>A UINT value that specifies whether to create an allocation that can be opened by any process. If <b>NonSecure</b> is set, secure and non-secure processes can open the allocation.</p>
<p>Setting this member is equivalent to setting the third bit of a 32-bit value (0x00000004).</p>
</dd>

### -field <b>CreateProtected</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the fourth bit of a 32-bit value (0x00000008).</p>
<p>Supported starting with Windows 7.</p>
</dd>

### -field <b>RestrictSharedAccess</b>

<dd>
<p>A UINT value that specifies whether to create a resource shared across all devices but with some restrictions.</p>
<p>Setting this member is equivalent to setting the fifth bit of a 32-bit value (0x00000010).</p>
<p>Supported starting with Windows 7.</p>
</dd>

### -field <b>ExistingSysMem</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the sixth bit of a 32-bit value (0x00000020).</p>
<p>Supported starting with Windows 7.</p>
</dd>

### -field <b>NtSecuritySharing</b>

<dd>
<p>A UINT value that specifies whether the allocation is shared with an NT handle, meaning that it  does not have a global <b>D3DKMT_HANDLE</b> kernel-mode handle to the resource.</p>
<p>If <b>NtSecuritySharing</b> is set to 1 (<b>TRUE</b>), the allocation is shared using the <a href="https://msdn.microsoft.com/library/windows/hardware/hh780251">D3DKMTShareObjects</a> function but does not have a global <b>D3DKMT_HANDLE</b> handle to the resource.</p>
<div class="alert"><b>Note</b>  If <b>NtSecuritySharing</b> is set to 1,  <b>CreateShared</b>  must be set to 1.</div>
<div> </div>
<p>For more information on using <b>NtSecuritySharing</b>, see the Remarks section.</p>
<p>Setting this member is equivalent to setting the seventh bit of a 32-bit value (0x00000040).</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>ReadOnly</b>

<dd>
<p>A UINT value that specifies whether the allocation can only be read from.</p>
<p>Setting this member is equivalent to setting the eighth bit of a 32-bit value (0x00000080).</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>CreateWriteCombined</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the seventh bit of a 32-bit value (0x00000100).</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>CreateCached</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the eighth bit of a 32-bit value (0x00000200).</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>SwapChainBackBuffer</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the seventh bit of a 32-bit value (0x00000100).</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the remaining 22 bits (0xFFFFFC00) of a 32-bit value to zeros.</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved and should be set to zero. Setting this member is equivalent to setting the remaining 26 bits (0xFFFFFFC0) of a 32-bit value to zeros.</p>
</dd>
</dl>

## -remarks
<p>Objects to be shared by using the <a href="https://msdn.microsoft.com/library/windows/hardware/hh780251">D3DKMTShareObjects</a> function must first be created with the <b>NtSecuritySharing</b> flag value set. This flag value is available in the <b>D3DKMT_CREATEALLOCATIONFLAGS</b>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh780254">D3DKMT_CREATEKEYEDMUTEX2_FLAGS</a>, and <a href="https://msdn.microsoft.com/library/windows/hardware/ff544662">D3DDDI_SYNCHRONIZATIONOBJECT_FLAGS</a> structures.</p>

<p>Drivers should follow these guidelines on <b>D3DKMT_CREATEALLOCATIONFLAGS</b> sharing flags:</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547798">D3DKMT_CREATEALLOCATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546807">D3DKMTCreateAllocation</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_CREATEALLOCATIONFLAGS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
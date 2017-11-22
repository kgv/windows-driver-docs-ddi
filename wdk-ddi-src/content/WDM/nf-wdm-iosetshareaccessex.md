---
UID: NF.wdm.IoSetShareAccessEx
title: IoSetShareAccessEx
author: windows-driver-content
description: The IoSetShareAccessEx routine sets the access rights for sharing the specified file object.
old-location: kernel\iosetshareaccessex.htm
ms.assetid: 4DCC4A37-0099-4C6F-B00D-B6CAA7D1EC68
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoSetShareAccessEx
req.alt-loc: ntoskrnl.lib,ntoskrnl.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ntoskrnl.lib
req.dll: 
req.irql: 
ms.keywords: IoSetShareAccessEx
req.iface: 
req.product: Windows 10 or later.
---

# IoSetShareAccessEx function



## -description
<p>The <b>IoSetShareAccessEx</b> routine sets the access rights for sharing the specified file object.</p>


## -syntax

````
VOID IoSetShareAccessEx(
  _In_     ACCESS_MASK   DesiredAccess,
  _In_     ULONG         DesiredShareAccess,
  _Inout_  PFILE_OBJECT  FileObject,
  _Out_    PSHARE_ACCESS ShareAccess,
  _In_opt_ PBOOLEAN      WritePermission 
);
````


## -parameters
<dl>

### -param <i>DesiredAccess</i> [in]

<dd>
<p>Specifies an <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> value that represents the type of access requested for the file object. See <a href="https://msdn.microsoft.com/library/windows/hardware/ff548418">IoCreateFile</a> for a complete list of system-defined <i>DesiredAccess</i> flags.</p>
</dd>

### -param <i>DesiredShareAccess</i> [in]

<dd>
<p>Specifies the type of share access to be set for the file object. This value can be zero, or any combination of the following flags:</p>
<dl>
<dd>
<p>FILE_SHARE_READ</p>
</dd>
<dd>
<p>FILE_SHARE_WRITE</p>
</dd>
<dd>
<p>FILE_SHARE_DELETE</p>
</dd>
</dl>
</dd>

### -param <i>FileObject</i> [in, out]

<dd>
<p>A pointer to the file object whose share access is being set or reset.</p>
</dd>

### -param <i>ShareAccess</i> [out]

<dd>
<p>A pointer to the <b>SHARE_ACCESS</b> structure that is associated with <i>FileObject</i>. Drivers should treat this structure as opaque.</p>
</dd>

### -param <i>WritePermission </i> [in, optional]

<dd>
<p>A pointer to the value that specifies whether the file object has write permission. This value is <b>TRUE</b> if the share has write permission; otherwise, it is <b>FALSE</b>. If  the value is <b>FALSE</b>  and the caller attempts to take exclusive read access, the write permission is downgraded to FILE_SHARE_READ.</p>
</dd>
</dl>

## -returns
<p>None.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ntoskrnl.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548418">IoCreateFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoSetShareAccessEx routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
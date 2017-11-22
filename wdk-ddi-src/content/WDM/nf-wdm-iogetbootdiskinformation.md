---
UID: NF.wdm.IoGetBootDiskInformation
title: IoGetBootDiskInformation
author: windows-driver-content
description: The IoGetBootDiskInformation routine returns information describing the boot and system disks.
old-location: kernel\iogetbootdiskinformation.htm
ms.assetid: 744d5eae-2bdf-46b0-9412-f73e55939d8b
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoGetBootDiskInformation
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
ms.keywords: IoGetBootDiskInformation
req.iface: 
req.product: Windows 10 or later.
---

# IoGetBootDiskInformation function



## -description
<p>The <b>IoGetBootDiskInformation</b> routine returns information describing the boot and system disks.</p>


## -syntax

````
NTSTATUS IoGetBootDiskInformation(
  _Inout_ PBOOTDISK_INFORMATION BootDiskInformation,
  _In_    ULONG                 Size
);
````


## -parameters
<dl>

### -param <i>BootDiskInformation</i> [in, out]

<dd>
<p>Pointer to a caller-allocated buffer that the routine uses to return information about the boot and system disks. The routine fills this buffer in with either a <a href="https://msdn.microsoft.com/library/windows/hardware/ff540652">BOOTDISK_INFORMATION</a> or a <a href="https://msdn.microsoft.com/library/windows/hardware/ff540653">BOOTDISK_INFORMATION_EX</a> structure.</p>
</dd>

### -param <i>Size</i> [in]

<dd>
<p>Specifies the size, in bytes, of the buffer specified by <i>BootDiskInformation</i>. Should be either <b>sizeof</b>(<b>BOOTDISK_INFORMATION</b>) or <b>sizeof</b>(<b>BOOTDISK_INFORMATION_EX</b>).</p>
</dd>
</dl>

## -returns
<p><b>IoGetBootDiskInformation</b> returns one of the following status values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The routine successfully returned the requested information in the buffer specified by <i>BootDiskInformation</i>.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The value of <i>Size</i> is less than the size, in bytes, of a <b>BOOTDISK_INFORMATION</b> structure.</p><dl>
<dt><b>STATUS_TOO_LATE</b></dt>
</dl><p>The driver called the routine after the system has already booted. Only boot and system drivers can call <b>IoGetBootDiskInformation</b>, and then only in their <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff540521">AddDevice</a> routines.</p>

<p> </p>

## -remarks
<p><b>IoGetBootDiskInformation</b> can be called only by a boot driver. This driver should call <b>IoGetBootDiskInformation</b> in a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561022">Reinitialize</a> callback routine that the driver registers by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff549494">IoRegisterBootDriverReinitialization</a> routine.</p>

<p>On Windows XP and later versions of Windows, if the <i>Size</i> parameter is <b>sizeof</b>(<b>BOOTDISK_INFORMATION_EX</b>) or larger, the routine returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff540653">BOOTDISK_INFORMATION_EX</a> structure in the <i>BootDiskInformation</i> buffer. Otherwise, if <i>Size</i> is at least <b>sizeof</b>(<b>BOOTDISK_INFORMATION</b>), the routine returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff540652">BOOTDISK_INFORMATION</a> structure.</p>

<p>On Windows 2000, the routine returns only the <b>BOOTDISK_INFORMATION</b> structure.</p>

<p><b>IoGetBootDiskInformation</b> can be called only by a boot driver. This driver should call <b>IoGetBootDiskInformation</b> in a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561022">Reinitialize</a> callback routine that the driver registers by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff549494">IoRegisterBootDriverReinitialization</a> routine.</p>

<p>On Windows XP and later versions of Windows, if the <i>Size</i> parameter is <b>sizeof</b>(<b>BOOTDISK_INFORMATION_EX</b>) or larger, the routine returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff540653">BOOTDISK_INFORMATION_EX</a> structure in the <i>BootDiskInformation</i> buffer. Otherwise, if <i>Size</i> is at least <b>sizeof</b>(<b>BOOTDISK_INFORMATION</b>), the routine returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff540652">BOOTDISK_INFORMATION</a> structure.</p>

<p>On Windows 2000, the routine returns only the <b>BOOTDISK_INFORMATION</b> structure.</p>

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
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540652">BOOTDISK_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540653">BOOTDISK_INFORMATION_EX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549494">IoRegisterBootDriverReinitialization</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561022">Reinitialize</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoGetBootDiskInformation routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
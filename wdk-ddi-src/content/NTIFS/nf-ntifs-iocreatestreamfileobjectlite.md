---
UID: NF.ntifs.IoCreateStreamFileObjectLite
title: IoCreateStreamFileObjectLite
author: windows-driver-content
description: The IoCreateStreamFileObjectLite routine creates a new stream file object, but does not cause an IRP_MJ_CLEANUP request to be sent to the file system driver stack.
old-location: ifsk\iocreatestreamfileobjectlite.htm
ms.assetid: 79c6438c-ba8c-4fc5-8c3f-5865a51869b7
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Microsoft Windows 2000 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCreateStreamFileObjectLite
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
req.irql: <= DISPATCH_LEVEL
ms.keywords: IoCreateStreamFileObjectLite
req.iface: 
---

# IoCreateStreamFileObjectLite function



## -description
<p>The <b>IoCreateStreamFileObjectLite</b> routine creates a new stream file object, but does not cause an IRP_MJ_CLEANUP request to be sent to the file system driver stack. </p>


## -syntax

````
PFILE_OBJECT IoCreateStreamFileObjectLite(
  _In_opt_ PFILE_OBJECT   FileObject,
  _In_opt_ PDEVICE_OBJECT DeviceObject
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in, optional]

<dd>
<p>A pointer to the file object to which the new stream file is related. This parameter is optional and can be <b>NULL</b>. </p>
</dd>

### -param <i>DeviceObject</i> [in, optional]

<dd>
<p>A pointer to a device object for the device on which the stream file is to be opened. If the caller specifies a non-<b>NULL</b> value for <i>FileObject</i>, the value of <i>DeviceObject</i> is ignored. Otherwise, the caller must specify a non-<b>NULL</b> value for <i>DeviceObject</i>. </p>
</dd>
</dl>

## -returns
<p><b>IoCreateStreamFileObjectLite</b> returns a pointer to the newly created stream file object.</p>

## -remarks
<p>File systems call <b>IoCreateStreamFileObjectLite</b> to create a new stream file object. A <i>stream file object</i> is identical to an ordinary file object, except that the FO_STREAM_FILE file object flag is set. </p>

<p>A stream file object is commonly used to represent an internal stream for a volume mounted by the file system. This <i>virtual volume file</i> permits the file system to view, change, and cache the volume's on-disk structure as if it were an ordinary file. In this case, the <i>DeviceObject</i> parameter in the call to <b>IoCreateStreamFileObjectLite</b> specifies the volume device object (VDO) for the volume. </p>

<p>A stream file object can also be used to represent an alternate data stream for accessing metadata, such as extended attributes or security descriptors, for an already opened file. In this case, the <i>FileObject</i> parameter in the call to <b>IoCreateStreamFileObjectLite</b> specifies an existing file object for the file. The newly created stream file object permits the file system to view, change, and cache the file's metadata as if it were an ordinary file. </p>

<p>When the stream file object is no longer needed, the caller must decrement its reference count by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>. When the stream file object's reference count reaches zero, an IRP_MJ_CLOSE request is sent to the file system driver stack for the volume. </p>

<p>File system filter driver writers should note that, unlike <a href="https://msdn.microsoft.com/library/windows/hardware/ff548296">IoCreateStreamFileObject</a>, <b>IoCreateStreamFileObjectLite</b> does not cause an IRP_MJ_CLEANUP request to be sent to the file system driver stack. For this reason, and because file systems often create stream file objects as a side effect of operations other than IRP_MJ_CREATE, it is difficult for filter drivers to reliably detect stream file object creation. Thus filter drivers should expect to receive IRP_MJ_CLOSE requests for previously unseen file objects. </p>

<p>If a pool allocation failure occurs, <b>IoCreateStreamFileObjectLite</b> raises a STATUS_INSUFFICIENT_RESOURCES exception. </p>

<p>File systems call <b>IoCreateStreamFileObjectLite</b> to create a new stream file object. A <i>stream file object</i> is identical to an ordinary file object, except that the FO_STREAM_FILE file object flag is set. </p>

<p>A stream file object is commonly used to represent an internal stream for a volume mounted by the file system. This <i>virtual volume file</i> permits the file system to view, change, and cache the volume's on-disk structure as if it were an ordinary file. In this case, the <i>DeviceObject</i> parameter in the call to <b>IoCreateStreamFileObjectLite</b> specifies the volume device object (VDO) for the volume. </p>

<p>A stream file object can also be used to represent an alternate data stream for accessing metadata, such as extended attributes or security descriptors, for an already opened file. In this case, the <i>FileObject</i> parameter in the call to <b>IoCreateStreamFileObjectLite</b> specifies an existing file object for the file. The newly created stream file object permits the file system to view, change, and cache the file's metadata as if it were an ordinary file. </p>

<p>When the stream file object is no longer needed, the caller must decrement its reference count by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>. When the stream file object's reference count reaches zero, an IRP_MJ_CLOSE request is sent to the file system driver stack for the volume. </p>

<p>File system filter driver writers should note that, unlike <a href="https://msdn.microsoft.com/library/windows/hardware/ff548296">IoCreateStreamFileObject</a>, <b>IoCreateStreamFileObjectLite</b> does not cause an IRP_MJ_CLEANUP request to be sent to the file system driver stack. For this reason, and because file systems often create stream file objects as a side effect of operations other than IRP_MJ_CREATE, it is difficult for filter drivers to reliably detect stream file object creation. Thus filter drivers should expect to receive IRP_MJ_CLOSE requests for previously unseen file objects. </p>

<p>If a pool allocation failure occurs, <b>IoCreateStreamFileObjectLite</b> raises a STATUS_INSUFFICIENT_RESOURCES exception. </p>

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
<p>This routine is available on Microsoft Windows 2000 and later. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548296">IoCreateStreamFileObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548303">IoCreateStreamFileObjectEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548608">IRP_MJ_CLEANUP</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550720">IRP_MJ_CLOSE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20IoCreateStreamFileObjectLite routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
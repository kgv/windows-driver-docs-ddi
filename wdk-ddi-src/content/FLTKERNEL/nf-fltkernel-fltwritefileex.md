---
UID: NF.fltkernel.FltWriteFileEx
title: FltWriteFileEx
author: windows-driver-content
description: FltWriteFileEx is used to write data to an open file, stream, or device. This function extends FltWriteFile to allow the optional use of an MDL for write data instead of a mapped buffer address.
old-location: ifsk\fltwritefileex.htm
ms.assetid: 18B2B486-5525-4132-96E8-EEA74342E0EA
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: The FltWriteFileEx function is available starting with  Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltWriteFileEx
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: PASSIVE_LEVEL
ms.keywords: FltWriteFileEx
req.iface: 
---

# FltWriteFileEx function



## -description
<p><b>FltWriteFileEx</b> is used to write data to an open file, stream, or device. This function extends <a href="https://msdn.microsoft.com/994b4a75-4581-423b-8b8f-17a64600fb74">FltWriteFile </a> to allow the optional use of an MDL for write data instead of a mapped buffer address.</p>


## -syntax

````
NTSTATUS FltWriteFileEx(
  _In_      PFLT_INSTANCE                    InitiatingInstance,
  _In_      PFILE_OBJECT                     FileObject,
  _In_opt_  PLARGE_INTEGER                   ByteOffset,
  _In_      ULONG                            Length,
  _In_      PVOID                            Buffer,
  _In_      FLT_IO_OPERATION_FLAGS           Flags,
  _Out_opt_ PULONG                           BytesWritten,
  _In_opt_  PFLT_COMPLETED_ASYNC_IO_CALLBACK CallbackRoutine,
  _In_opt_  PVOID                            CallbackContext,
  _In_opt_  PULONG                           Key,
  _In_opt_  PMDL                             Mdl
);
````


## -parameters
<dl>

### -param <i>InitiatingInstance</i> [in]

<dd>
<p>An opaque instance pointer for the minifilter driver instance that is initiating the write request. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>FileObject</i> [in]

<dd>
<p>A pointer to a file object for the file that the data is to be written to. This file object must be currently open. Calling <b>FltWriteFileEx</b> when the file object is not yet open or is no longer open (for example, in a pre-create or post-cleanup callback routine) causes the system to ASSERT on a checked build. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>ByteOffset</i> [in, optional]

<dd>
<p>A pointer to a caller-allocated variable that specifies the starting byte offset within the file where the write operation is to begin. </p>
<p>If this offset is supplied, or if the <b>FLTFL_IO_OPERATION_DO_NOT_UPDATE_BYTE_OFFSET</b> flag is specified in the <i>Flags</i> parameter, <b>FltWriteFileEx</b> does not update the file object's <b>CurrentByteOffset</b> field. </p>
<p>If the file object that <i>FileObject</i> points to was opened for synchronous I/O, the caller of <b>FltWriteFileEx</b> can specify that the current file position offset be used instead of an explicit <i>ByteOffset</i> value by setting this parameter to <b>NULL</b>. If the current file position is used, <b>FltWriteFileEx</b> updates the file object's <b>CurrentByteOffset</b> field by adding the number of bytes written when it completes the write operation. </p>
<p>If the file object that <i>FileObject</i> points to was opened for asynchronous I/O, this parameter is required and cannot be <b>NULL</b>. </p>
<p>
<div class="alert"><b>Note</b>  The <b>FltWriteFileEx</b> function does not support the FILE_WRITE_TO_END_OF_FILE flag.</div>
<div> </div>
</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>The size, in bytes, of the buffer that the <i>Buffer</i> parameter points to. </p>
</dd>

### -param <i>Buffer</i> [in]

<dd>
<p>A pointer to a buffer that contains the data to be written to the file. If the file is opened for noncached I/O, this buffer be must be aligned in accordance with the alignment requirement of the underlying storage device. Minifilter drivers can allocate such an aligned buffer by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff541762">FltAllocatePoolAlignedWithTag</a>. </p>
<p>If an MDL is provided in <i>Mdl</i>, <i>Buffer</i> must be NULL.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>A bitmask of flags that specify the type of write operation to be performed. </p>
<table>
<tr>
<th>Flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p><b>FLTFL_IO_OPERATION_DO_NOT_UPDATE_BYTE_OFFSET</b></p>
</td>
<td>
<p>Minifilter drivers can set this flag to specify that <b>FltWriteFileEx</b>  will not update the file object's <b>CurrentByteOffset</b> field. </p>
</td>
</tr>
<tr>
<td>
<p><b>FLTFL_IO_OPERATION_NON_CACHED</b></p>
</td>
<td>
<p>Minifilter drivers can set this flag to specify a noncached write, even if the file object was not opened with <b>FILE_NO_INTERMEDIATE_BUFFERING</b>. </p>
</td>
</tr>
<tr>
<td>
<p><b>FLTFL_IO_OPERATION_PAGING</b></p>
</td>
<td>
<p>Minifilter drivers can set this flag to specify a paging write. </p>
</td>
</tr>
<tr>
<td>
<p><b>FLTFL_IO_OPERATION_SYNCHRONOUS_PAGING</b></p>
</td>
<td>
<p>Minifilter drivers can set this flag to specify a synchronous paging I/O write. Minifilter drivers that set this flag must also set the <b>FLTFL_IO_OPERATION_PAGING</b> flag.</p>
<p>This flag is available starting with Windows Vista.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -param <i>BytesWritten</i> [out, optional]

<dd>
<p>A pointer to a caller-allocated variable that receives the number of bytes written to the file. If <i>CallbackRoutine</i> is not <b>NULL</b>, this parameter is ignored. Otherwise, this parameter is optional and can be <b>NULL</b>. </p>
</dd>

### -param <i>CallbackRoutine</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff551067">PFLT_COMPLETED_ASYNC_IO_CALLBACK</a>-typed callback routine to call when the write operation is complete. This parameter is optional and can be <b>NULL</b>. </p>
</dd>

### -param <i>CallbackContext</i> [in, optional]

<dd>
<p>A context pointer to be passed to the routine in <i>CallbackRoutine</i> if one is present. This parameter is optional and can be <b>NULL</b>. If <i>CallbackRoutine</i> is <b>NULL</b>, this parameter is ignored. </p>
</dd>

### -param <i>Key</i> [in, optional]

<dd>
<p>An optional key associated with a file object lock.</p>
</dd>

### -param <i>Mdl</i> [in, optional]

<dd>
<p>An optional MDL that describes the data to write. If a buffer is provided in <i>Buffer</i>, then <i>Mdl</i> must be NULL.</p>
</dd>
</dl>

## -returns
<p><b>FltWriteFileEx</b> returns the NTSTATUS value that was returned by the file system. </p>

## -remarks
<p>A minifilter driver calls <b>FltWriteFileEx</b> to write data to an open file. </p>

<p><b>FltWriteFileEx</b> causes a write request to be sent to the minifilter driver instances attached below the initiating instance and to the file system. The specified instance and the instances attached above it do not receive the write request. </p>

<p><b>FltWriteFileEx</b> performs noncached I/O if either of the following is true: </p>

<p>The caller set the <b>FLTFL_IO_OPERATION_NON_CACHED</b> flag in the <i>Flags</i> parameter. </p>

<p>The file object was opened for noncached I/O. Usually, this is done by specifying the <b>FILE_NO_INTERMEDIATE_BUFFERING</b><b>CreateOptions</b> flag in the preceding call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff541935">FltCreateFile</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff541937">FltCreateFileEx</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff566424">ZwCreateFile</a>. </p>

<p>Noncached I/O imposes the following restrictions on the parameter values passed to <b>FltWriteFileEx</b>: </p>

<p>The buffer that the <i>Buffer</i> parameter points to must be aligned in accordance with the alignment requirement of the underlying storage device. To allocate such an aligned buffer, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541762">FltAllocatePoolAlignedWithTag</a>. </p>

<p>The byte offset that the <i>ByteOffset</i> parameter points to must be a nonnegative multiple of the volume's sector size. </p>

<p>The length specified in the <i>Length</i> parameter must be a nonnegative multiple of the volume's sector size. </p>

<p>If the value of the <i>CallbackRoutine</i> parameter is not <b>NULL</b>, the write operation is performed asynchronously. </p>

<p>If the value of the <i>CallbackRoutine</i> parameter is <b>NULL</b>, the write operation is performed synchronously. That is, <b>FltWriteFileEx</b> waits until the write operation is complete before returning. This is true even if the file object that <i>FileObject</i> points to was opened for asynchronous I/O. </p>

<p>If multiple threads call <b>FltWriteFileEx</b> for the same file object, and the file object was opened for synchronous I/O, the filter manager does not attempt to serialize I/O on the file. In this respect, <b>FltWriteFileEx</b> differs from <a href="https://msdn.microsoft.com/library/windows/hardware/ff567121">ZwWriteFile</a>. </p>

<p>The <i>Mdl</i> parameter is provided as a convenience when a minifilter already has an MDL available. The MDL is used directly and the additional step of mapping an address for <i>Buffer</i> can be avoided.</p>

<p>A minifilter driver calls <b>FltWriteFileEx</b> to write data to an open file. </p>

<p><b>FltWriteFileEx</b> causes a write request to be sent to the minifilter driver instances attached below the initiating instance and to the file system. The specified instance and the instances attached above it do not receive the write request. </p>

<p><b>FltWriteFileEx</b> performs noncached I/O if either of the following is true: </p>

<p>The caller set the <b>FLTFL_IO_OPERATION_NON_CACHED</b> flag in the <i>Flags</i> parameter. </p>

<p>The file object was opened for noncached I/O. Usually, this is done by specifying the <b>FILE_NO_INTERMEDIATE_BUFFERING</b><b>CreateOptions</b> flag in the preceding call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff541935">FltCreateFile</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff541937">FltCreateFileEx</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff566424">ZwCreateFile</a>. </p>

<p>Noncached I/O imposes the following restrictions on the parameter values passed to <b>FltWriteFileEx</b>: </p>

<p>The buffer that the <i>Buffer</i> parameter points to must be aligned in accordance with the alignment requirement of the underlying storage device. To allocate such an aligned buffer, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541762">FltAllocatePoolAlignedWithTag</a>. </p>

<p>The byte offset that the <i>ByteOffset</i> parameter points to must be a nonnegative multiple of the volume's sector size. </p>

<p>The length specified in the <i>Length</i> parameter must be a nonnegative multiple of the volume's sector size. </p>

<p>If the value of the <i>CallbackRoutine</i> parameter is not <b>NULL</b>, the write operation is performed asynchronously. </p>

<p>If the value of the <i>CallbackRoutine</i> parameter is <b>NULL</b>, the write operation is performed synchronously. That is, <b>FltWriteFileEx</b> waits until the write operation is complete before returning. This is true even if the file object that <i>FileObject</i> points to was opened for asynchronous I/O. </p>

<p>If multiple threads call <b>FltWriteFileEx</b> for the same file object, and the file object was opened for synchronous I/O, the filter manager does not attempt to serialize I/O on the file. In this respect, <b>FltWriteFileEx</b> differs from <a href="https://msdn.microsoft.com/library/windows/hardware/ff567121">ZwWriteFile</a>. </p>

<p>The <i>Mdl</i> parameter is provided as a convenience when a minifilter already has an MDL available. The MDL is used directly and the additional step of mapping an address for <i>Buffer</i> can be avoided.</p>

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
<p>The <b>FltWriteFileEx</b> function is available starting with  Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include Fltkernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>FltMgr.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Fltmgr.sys</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541762">FltAllocatePoolAlignedWithTag</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541935">FltCreateFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541937">FltCreateFileEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544286">FltReadFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451034">FltReadFileEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558679">ObReferenceObjectByHandle</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551067">PFLT_COMPLETED_ASYNC_IO_CALLBACK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567121">ZwWriteFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltWriteFileEx function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
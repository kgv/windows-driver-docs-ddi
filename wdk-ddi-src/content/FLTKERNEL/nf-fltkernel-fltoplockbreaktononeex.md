---
UID: NF.fltkernel.FltOplockBreakToNoneEx
title: FltOplockBreakToNoneEx
author: windows-driver-content
description: The FltOplockBreakToNoneEx routine breaks all opportunistic locks (oplocks) immediately without regard for any oplock key.
old-location: ifsk\fltoplockbreaktononeex.htm
ms.assetid: 748951e3-9642-4c98-a3b0-5f6b18519bd4
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: The FltOplockBreakToNoneEx routine is available starting with Windows 7.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltOplockBreakToNoneEx
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
req.irql: <= APC_LEVEL
ms.keywords: FltOplockBreakToNoneEx
req.iface: 
---

# FltOplockBreakToNoneEx function



## -description
<p>The <b>FltOplockBreakToNoneEx</b> routine breaks all opportunistic locks (oplocks) immediately without regard for any oplock key. </p>


## -syntax

````
FLT_PREOP_CALLBACK_STATUS FltOplockBreakToNoneEx(
  _In_     POPLOCK                                 Oplock,
  _In_     PFLT_CALLBACK_DATA                      CallbackData,
  _In_     ULONG                                   Flags,
  _In_opt_ PVOID                                   Context,
  _In_opt_ PFLTOPLOCK_WAIT_COMPLETE_ROUTINE        WaitCompletionRoutine,
  _In_opt_ PFLTOPLOCK_PREPOST_CALLBACKDATA_ROUTINE PrePostCallbackDataRoutine
);
````


## -parameters
<dl>

### -param <i>Oplock</i> [in]

<dd>
<p>An opaque oplock pointer for the file. This pointer must have been initialized by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>. </p>
</dd>

### -param <i>CallbackData</i> [in]

<dd>
<p>A pointer to the callback data (<a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a>) structure for the I/O operation. </p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>A bitmask for the associated file I/O operation. A minifilter driver sets bits to specify the behavior of <b>FltOplockBreakToNoneEx</b>. The <i>Flags</i> parameter has the following options: </p>
<p></p>
<dl>

### -param <a id="OPLOCK_FLAG_COMPLETE_IF_OPLOCKED__0x00000001_"></a><a id="oplock_flag_complete_if_oplocked__0x00000001_"></a><a id="OPLOCK_FLAG_COMPLETE_IF_OPLOCKED__0X00000001_"></a>OPLOCK_FLAG_COMPLETE_IF_OPLOCKED (0x00000001)

<dd>
<p>Allows an oplock break to proceed without blocking or pending the operation that caused the oplock break. Typically, this flag is only used if the I/O operation that is represented by the callback data that the <i>CallbackData</i> parameter points to is an IRP_MJ_CREATE operation. </p>
</dd>
</dl>
</dd>

### -param <i>Context</i> [in, optional]

<dd>
<p>A pointer to caller-defined context information to be passed to the callback routines that the <i>WaitCompletionRoutine</i> and <i>PrePostCallbackDataRoutine </i>parameters point to. </p>
</dd>

### -param <i>WaitCompletionRoutine</i> [in, optional]

<dd>
<p>A pointer to a caller-supplied callback routine. If an oplock break is in progress, this routine is called when the break is completed. This parameter is optional and can be <b>NULL</b>. If it is <b>NULL</b>, the caller is put into a wait state until the oplock break is completed. </p>
<p>This routine is declared as follows: </p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef VOID
(*PFLTOPLOCK_WAIT_COMPLETE_ROUTINE) (
    __in PFLT_CALLBACK_DATA CallbackData,
 __in_opt PVOID Context
      );</pre>
</td>
</tr>
</table></span></div>
<p>This routine has the following parameters: </p>
<p></p>
<dl>

### -param <a id="CallbackData"></a><a id="callbackdata"></a><a id="CALLBACKDATA"></a><i>CallbackData</i>

<dd>
<p>A pointer to the callback data structure for the I/O operation. </p>
</dd>

### -param <a id="Context"></a><a id="context"></a><a id="CONTEXT"></a><i>Context</i>

<dd>
<p>A context information pointer that was passed in the <i>Context</i> parameter to <b>FltOplockBreakToNoneEx</b>. </p>
</dd>
</dl>
</dd>

### -param <i>PrePostCallbackDataRoutine</i> [in, optional]

<dd>
<p>A pointer to a caller-supplied callback routine to be called if the I/O operation is to be pended. The routine is called before the oplock package pends the IRP. This parameter is optional and can be <b>NULL</b>. </p>
<p>This routine is declared as follows: </p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef VOID
(*PFLTOPLOCK_PREPOST_CALLBACKDATA_ROUTINE) (
    __in PFLT_CALLBACK_DATA CallbackData,
 __in_opt PVOID Context
      );</pre>
</td>
</tr>
</table></span></div>
<p>This routine has the following parameters: </p>
<p></p>
<dl>

### -param <a id="CallbackData"></a><a id="callbackdata"></a><a id="CALLBACKDATA"></a><i>CallbackData</i>

<dd>
<p>A pointer to the callback data structure for the I/O operation. </p>
</dd>

### -param <a id="Context"></a><a id="context"></a><a id="CONTEXT"></a><i>Context</i>

<dd>
<p>A context information pointer that was passed in the <i>Context</i> parameter to <b>FltOplockBreakToNoneEx</b>. </p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p><b>FltOplockBreakToNoneEx</b> returns one of the following FLT_PREOP_CALLBACK_STATUS codes: </p><dl>
<dt><b>FLT_PREOP_COMPLETE</b></dt>
</dl><p><b>FltOplockBreakToNoneEx</b> encountered a pool allocation failure, or a call to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff547108">FsRtlOplockBreakToNoneEx</a> function returned an error. <b>FltOplockBreakToNoneEx</b> will set the error code in the <b>Status</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550671">IO_STATUS_BLOCK</a> structure. The IO_STATUS_BLOCK structure is specified in the <b>IoStatus</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a> callback data structure. The <i>CallbackData</i> parameter points to this FLT_CALLBACK_DATA. </p><dl>
<dt><b>FLT_PREOP_PENDING</b></dt>
</dl><p>An oplock break was initiated, which caused the Filter Manager to post the I/O operation to a work queue. The I/O operation is represented by the callback data that the <i>CallbackData</i> parameter points to. </p><dl>
<dt><b>FLT_PREOP_SUCCESS_WITH_CALLBACK</b></dt>
</dl><p>The callback data that the <i>CallbackData</i> parameter points to was not pended, and the I/O operation was performed immediately. Be aware that if the caller specified OPLOCK_FLAG_COMPLETE_IF_OPLOCKED in the <i>Flags</i> parameter, an oplock break might actually be in progress even though the I/O operation was not pended. To determine whether this is the situation, the caller should check for STATUS_OPLOCK_BREAK_IN_PROGRESS in the <b>Status</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550671">IO_STATUS_BLOCK</a> structure. The IO_STATUS_BLOCK structure is specified in the <b>IoStatus</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a> callback data structure. </p>

<p> </p>

## -remarks
<p>For more information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

<p>For more information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

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
<p>The FltOplockBreakToNoneEx routine is available starting with Windows 7. </p>
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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547108">FsRtlOplockBreakToNoneEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550671">IO_STATUS_BLOCK</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltOplockBreakToNoneEx routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
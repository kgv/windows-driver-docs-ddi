---
UID: NF.fltkernel.FltApplyPriorityInfoThread
title: FltApplyPriorityInfoThread
author: windows-driver-content
description: The FltApplyPriorityInfoThread routine is used by a minifilter driver to apply priority information to a thread.
old-location: ifsk\fltapplypriorityinfothread.htm
ms.assetid: 62fd46a8-ee34-4c61-8e87-7fbe1a4622be
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows Vista and later versions of Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltApplyPriorityInfoThread
req.alt-loc: Fltmgr.lib,Fltmgr.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fltmgr.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: FltApplyPriorityInfoThread
req.iface: 
---

# FltApplyPriorityInfoThread function



## -description
<p>The <b>FltApplyPriorityInfoThread</b> routine is used by a minifilter driver to apply priority information to a thread.</p>


## -syntax

````
NTSTATUS FltApplyPriorityInfoThread(
  _In_      PIO_PRIORITY_INFO InputPriorityInfo,
  _Out_opt_ PIO_PRIORITY_INFO OutputPriorityInfo,
  _In_      PETHREAD          Thread
);
````


## -parameters
<dl>

### -param <i>InputPriorityInfo</i> [in]

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548568">IO_PRIORITY_INFO</a> structure that is used to set the priority state of the given thread.  This IO_PRIORITY_INFO structure must have its members set by an appropriate routine - see the following Remarks section.  This parameter is required and cannot be <b>NULL</b>.</p>
</dd>

### -param <i>OutputPriorityInfo</i> [out, optional]

<dd>
<p>An optional pointer to an IO_PRIORITY_INFO structure used to receive the priority state of the thread before the <i>InputPriorityInfo</i> priority information is applied to the thread by <b>FltApplyPriorityInfoThread</b>.  This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>Thread</i> [in]

<dd>
<p>A pointer to the thread in which to apply the <i>InputPriorityInfo</i> priority information to.  This parameter is required and cannot be <b>NULL</b>. </p>
</dd>
</dl>

## -returns
<p>If the thread priority information, pointed to by the <i>InputPriorityInfo</i> parameter, is successfully applied to the given thread, the <b>FltApplyPriorityInfoThread</b> routine returns STATUS_SUCCESS.  Otherwise, it returns an appropriate NTSTATUS value, such as one of the following:</p><dl>
<dt><b>STATUS_INVALID_PARAMETER_1</b></dt>
</dl><p>The structure pointed to by the <i>InputPriorityInfo</i> parameter was initialized but one or more of its member values are invalid.  This is an error code.</p>

<p> </p>

## -remarks
<p>This routine is available starting with Windows Vista.</p>

<p>The <b>FltApplyPriorityInfoThread</b> routine sets the I/O priority, paging priority and thread priority of the given thread based on the member values of the IO_PRIORITY_INFO structure pointed to by the <i>InputPriorityInfo</i> parameter.  This allows a previously saved set of priority information, acquired by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544354">FltRetrieveIoPriorityInfo</a> or <b>FltApplyPriorityInfoThread</b> routine, to be applied to a thread.</p>

<p>The original values of the target thread, before the <i>InputPriorityInfo</i> priority values are applied by the <b>FltApplyPriorityInfoThread</b> routine, can be saved if a valid <i>OutputPriorityInfo</i> pointer is supplied.  Note that the structure pointed to by the <i>OutputPriorityInfo</i> parameter need not be initialized.</p>

<p>It is safe to provide the same pointer to a single IO_PRIORITY_INFO structure for both the <i>InputPriorityInfo</i> and <i>OutputPriorityInfo</i> parameters.</p>

<p> Call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544354">FltRetrieveIoPriorityInfo</a> routine.</p>

<p> Ensure that the current <i>InputPriorityInfo</i> parameter was the <i>OutputPriorityInfo</i> parameter in a prior call to the <b>FltApplyPriorityInfoThread</b> routine.</p>

<p>This routine is available starting with Windows Vista.</p>

<p>The <b>FltApplyPriorityInfoThread</b> routine sets the I/O priority, paging priority and thread priority of the given thread based on the member values of the IO_PRIORITY_INFO structure pointed to by the <i>InputPriorityInfo</i> parameter.  This allows a previously saved set of priority information, acquired by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544354">FltRetrieveIoPriorityInfo</a> or <b>FltApplyPriorityInfoThread</b> routine, to be applied to a thread.</p>

<p>The original values of the target thread, before the <i>InputPriorityInfo</i> priority values are applied by the <b>FltApplyPriorityInfoThread</b> routine, can be saved if a valid <i>OutputPriorityInfo</i> pointer is supplied.  Note that the structure pointed to by the <i>OutputPriorityInfo</i> parameter need not be initialized.</p>

<p>It is safe to provide the same pointer to a single IO_PRIORITY_INFO structure for both the <i>InputPriorityInfo</i> and <i>OutputPriorityInfo</i> parameters.</p>

<p> Call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544354">FltRetrieveIoPriorityInfo</a> routine.</p>

<p> Ensure that the current <i>InputPriorityInfo</i> parameter was the <i>OutputPriorityInfo</i> parameter in a prior call to the <b>FltApplyPriorityInfoThread</b> routine.</p>

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
<p>Available in Microsoft Windows Vista and later versions of Windows operating systems.</p>
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
<dt>Fltmgr.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543065">FltGetIoPriorityHint</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543068">FltGetIoPriorityHintFromCallbackData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543074">FltGetIoPriorityHintFromFileObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543080">FltGetIoPriorityHintFromThread</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544354">FltRetrieveIoPriorityInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544526">FltSetIoPriorityHintIntoCallbackData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544530">FltSetIoPriorityHintIntoFileObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544534">FltSetIoPriorityHintIntoThread</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548568">IO_PRIORITY_INFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltApplyPriorityInfoThread routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
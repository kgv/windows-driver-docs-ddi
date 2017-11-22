---
UID: NF.fltkernel.FltSetIoPriorityHintIntoThread
title: FltSetIoPriorityHintIntoThread
author: windows-driver-content
description: The FltSetIoPriorityHintIntoThread routine is used by a minifilter driver to set the IO priority information in a thread.
old-location: ifsk\fltsetiopriorityhintintothread.htm
ms.assetid: 924fadbe-2703-43f8-985c-db5a7bb960a6
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: FltKernel.h
req.target-type: Universal
req.target-min-winverclnt: Available in starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltSetIoPriorityHintIntoThread
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
req.irql: <= DISPATCH_LEVEL
ms.keywords: FltSetIoPriorityHintIntoThread
req.iface: 
---

# FltSetIoPriorityHintIntoThread function



## -description
<p>The <b>FltSetIoPriorityHintIntoThread</b> routine is used by a minifilter driver to set the IO priority information in a thread.</p>


## -syntax

````
NTSTATUS FltSetIoPriorityHintIntoThread(
  _In_ PETHREAD         Thread,
  _In_ IO_PRIORITY_HINT PriorityHint
);
````


## -parameters
<dl>

### -param <i>Thread</i> [in]

<dd>
<p>A pointer to the thread to modify. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>PriorityHint</i> [in]

<dd>
<p>The  <a href="https://msdn.microsoft.com/library/windows/hardware/ff550594">IO_PRIORITY_HINT</a> enumeration value to set for the thread information pointed to by <i>Thread</i>.</p>
</dd>
</dl>

## -returns
<p>If the IO Priority value passed to the <i>PriorityHint</i> parameter is successfully applied to the <i>Thread</i>, <b>FltSetIoPriorityHintIntoThread</b> returns STATUS_SUCCESS. Otherwise, it returns an appropriate NTSTATUS value, such as one of the following:</p><dl>
<dt><b>STATUS_INVALID_PARAMETER </b></dt>
</dl><p>The value of the <i>PriorityHint</i> parameter is invalid. This is an error code. </p>

<p> </p>

## -remarks
<p>This routine is NONPAGED and can be called from paging IO paths.</p>

<p>This routine is NONPAGED and can be called from paging IO paths.</p>

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
<p>Available in starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include FltKernel.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541766">FltApplyPriorityInfoThread</a>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550594">IO_PRIORITY_HINT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltSetIoPriorityHintIntoThread routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
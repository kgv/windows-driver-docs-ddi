---
UID: NF.fltkernel.FltDeleteTransactionContext
title: FltDeleteTransactionContext
author: windows-driver-content
description: The FltDeleteTransactionContext routine removes a context from a given transaction and marks the context for deletion.
old-location: ifsk\fltdeletetransactioncontext.htm
ms.assetid: 120285ff-1cb4-4570-a1e7-0a7d22b43560
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltDeleteTransactionContext
req.alt-loc: FltMgr.lib,FltMgr.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: FltDeleteTransactionContext
req.iface: 
---

# FltDeleteTransactionContext function



## -description
<p>The <b>FltDeleteTransactionContext</b> routine removes a context from a given transaction and marks the context for deletion. </p>


## -syntax

````
NTSTATUS FltDeleteTransactionContext(
  _In_      PFLT_INSTANCE Instance,
  _In_      PKTRANSACTION Transaction,
  _Out_opt_ PFLT_CONTEXT  *OldContext
);
````


## -parameters
<dl>

### -param <i>Instance</i> [in]

<dd>
<p>Opaque instance pointer for the caller. </p>
</dd>

### -param <i>Transaction</i> [in]

<dd>
<p>Opaque transaction pointer for the transaction whose context is being deleted. </p>
</dd>

### -param <i>OldContext</i> [out, optional]

<dd>
<p>Pointer to a caller-allocated variable that receives the address of the deleted context. This parameter is optional and can be <b>NULL</b>. If <i>OldContext</i> is not <b>NULL</b> and does not point to NULL_CONTEXT, the caller is responsible for calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff544314">FltReleaseContext</a> to release this context when it is no longer needed. </p>
</dd>
</dl>

## -returns
<p><b>FltDeleteTransactionContext</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value such as the following: </p><dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl><p>No matching context was found. This is an error code. </p>

<p> </p>

## -remarks
<p>This routine is available on Windows Vista and later. </p>

<p>Because contexts are reference-counted, it is not usually necessary for a minifilter driver to call a routine such as <b>FltDeleteTransactionContext</b> to explicitly delete a context. </p>

<p>A minifilter driver calls <b>FltDeleteTransactionContext</b> to remove a context from a transaction and mark the context for deletion. The context is usually freed immediately unless there is an outstanding reference on it (for example, because the context is still being used by another thread). </p>

<p>To allocate a new transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541710">FltAllocateContext</a>. </p>

<p>To retrieve a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543175">FltGetTransactionContext</a>. </p>

<p>To set a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff544554">FltSetTransactionContext</a>. </p>

<p>This routine is available on Windows Vista and later. </p>

<p>Because contexts are reference-counted, it is not usually necessary for a minifilter driver to call a routine such as <b>FltDeleteTransactionContext</b> to explicitly delete a context. </p>

<p>A minifilter driver calls <b>FltDeleteTransactionContext</b> to remove a context from a transaction and mark the context for deletion. The context is usually freed immediately unless there is an outstanding reference on it (for example, because the context is still being used by another thread). </p>

<p>To allocate a new transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541710">FltAllocateContext</a>. </p>

<p>To retrieve a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543175">FltGetTransactionContext</a>. </p>

<p>To set a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff544554">FltSetTransactionContext</a>. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541710">FltAllocateContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541875">FltCommitComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541960">FltDeleteContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542053">FltEnlistInTransaction</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543175">FltGetTransactionContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543424">FltPrepareComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543425">FltPrePrepareComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544314">FltReleaseContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544366">FltRollbackComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544374">FltRollbackEnlistment</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544554">FltSetTransactionContext</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltDeleteTransactionContext routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
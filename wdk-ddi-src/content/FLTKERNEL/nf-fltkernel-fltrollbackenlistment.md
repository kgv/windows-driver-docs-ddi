---
UID: NF.fltkernel.FltRollbackEnlistment
title: FltRollbackEnlistment
author: windows-driver-content
description: The FltRollbackEnlistment routine rolls back or aborts a transaction on behalf of a minifilter driver.
old-location: ifsk\fltrollbackenlistment.htm
ms.assetid: a63ebd95-801b-4de2-963e-392e6d90eb9f
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Windows Vista and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltRollbackEnlistment
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
ms.keywords: FltRollbackEnlistment
req.iface: 
---

# FltRollbackEnlistment function



## -description
<p>The <b>FltRollbackEnlistment</b> routine rolls back or aborts a transaction on behalf of a minifilter driver. </p>


## -syntax

````
NTSTATUS FltRollbackEnlistment(
  _In_     PFLT_INSTANCE Instance,
  _In_     PKTRANSACTION Transaction,
  _In_opt_ PFLT_CONTEXT  TransactionContext
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
<p>Opaque transaction pointer for the transaction. </p>
</dd>

### -param <i>TransactionContext</i> [in, optional]

<dd>
<p>Pointer to the minifilter driver's transaction context. </p>
</dd>
</dl>

## -returns
<p><b>FltRollbackEnlistment</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value, such as one of the following: </p><dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl><p>The minifilter driver did not set a context on the transaction. This is an error code. </p><dl>
<dt><b>STATUS_TRANSACTION_REQUEST_NOT_VALID</b></dt>
</dl><p>The transaction rollback request is not allowed for this enlistment. This is an error code. </p>

<p> </p>

## -remarks
<p>A minifilter driver that is enlisted in a transaction can call <b>FltRollbackEnlistment</b> to roll back or abort the transaction. </p>

<p>To enlist in a transaction, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542053">FltEnlistInTransaction</a>. </p>

<p>To allocate a new transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541710">FltAllocateContext</a>. </p>

<p>To retrieve a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543175">FltGetTransactionContext</a>. </p>

<p>To delete a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542023">FltDeleteTransactionContext</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff541960">FltDeleteContext</a>. </p>

<p>To set a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff544554">FltSetTransactionContext</a>. </p>

<p>A minifilter driver that is enlisted in a transaction can call <b>FltRollbackEnlistment</b> to roll back or abort the transaction. </p>

<p>To enlist in a transaction, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542053">FltEnlistInTransaction</a>. </p>

<p>To allocate a new transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541710">FltAllocateContext</a>. </p>

<p>To retrieve a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543175">FltGetTransactionContext</a>. </p>

<p>To delete a transaction context, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542023">FltDeleteTransactionContext</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff541960">FltDeleteContext</a>. </p>

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
<p>Version</p>
</th>
<td width="70%">
<p>This routine is available on Windows Vista and later. </p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541710">FltAllocateContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541875">FltCommitComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541960">FltDeleteContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542023">FltDeleteTransactionContext</a>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544554">FltSetTransactionContext</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltRollbackEnlistment routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
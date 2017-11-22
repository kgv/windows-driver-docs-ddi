---
UID: NS.fltkernel._FLT_RELATED_OBJECTS
title: FLT_RELATED_OBJECTS
author: windows-driver-content
description: The FLT_RELATED_OBJECTS structure contains opaque pointers for the objects associated with an operation.
old-location: ifsk\flt_related_objects.htm
ms.assetid: dd1730f5-58ff-4d0d-9a00-17cd1fe36c5f
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FLT_RELATED_OBJECTS
req.alt-loc: fltkernel.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: FLT_RELATED_OBJECTS, FLT_RELATED_OBJECTS, *PFLT_RELATED_OBJECTS
req.iface: 
---

# FLT_RELATED_OBJECTS structure



## -description
<p>The FLT_RELATED_OBJECTS structure contains opaque pointers for the objects associated with an operation. </p>


## -syntax

````
typedef struct _FLT_RELATED_OBJECTS {
  const USHORT        Size;
  const USHORT        TransactionContext;
  const PFLT_FILTER   Filter;
  const PFLT_VOLUME   Volume;
  const PFLT_INSTANCE Instance;
  const PFILE_OBJECT  FileObject;
  const PKTRANSACTION Transaction;
} FLT_RELATED_OBJECTS, *PFLT_RELATED_OBJECTS;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Size, in bytes, of the FLT_RELATED_OBJECTS structure. </p>
</dd>

### -field <b>TransactionContext</b>

<dd>
<p>Opaque member that contains the transaction miniversion ID value if the <b>Transaction</b> member is not <b>NULL</b>.  If <b>Transaction</b> is <b>NULL</b>, the value of <b>TransactionContext</b> is undefined.</p>
</dd>

### -field <b>Filter</b>

<dd>
<p>Opaque filter pointer for the minifilter driver whose callback routine is being called for the operation. This pointer uniquely identifies the minifilter driver and remains constant as long as the minifilter driver is loaded. </p>
</dd>

### -field <b>Volume</b>

<dd>
<p>Opaque volume pointer for the volume that is associated with the operation. This pointer uniquely identifies the volume and remains constant over the lifetime of the volume device stack. </p>
</dd>

### -field <b>Instance</b>

<dd>
<p>Opaque instance pointer for the minifilter driver instance that is associated with the operation. This pointer uniquely identifies the instance and remains constant as long as the instance is attached to a volume. </p>
</dd>

### -field <b>FileObject</b>

<dd>
<p>Pointer to the file object, if any, for the operation. </p>
</dd>

### -field <b>Transaction</b>

<dd>
<p>On Windows Vista and later, this member is an opaque transaction pointer to the transaction that is associated with the operation. The operation will be part of a transaction if the value of this member is not <b>NULL</b>.  If the value of this member is <b>NULL</b>, the operation will not be part of a transaction.  On Windows operating systems before Windows Vista, the value of this member will always be <b>NULL</b>. </p>
</dd>
</dl>

## -remarks
<p>The FLT_RELATED_OBJECTS structure is allocated by the filter manager and contains opaque pointers for the objects associated with an I/O operation or an instance setup or teardown operation. </p>

<p>The contents of the FLT_RELATED_OBJECTS structure are set by the filter manager. Minifilter drivers cannot directly modify the contents of this structure. However, if a minifilter driver modifies the target instance or target file object for an I/O operation in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544638">FLT_IO_PARAMETER_BLOCK</a> structure for the operation, the filter manager modifies the value of the corresponding <b>Instance</b> or <b>FileObject</b> member of the FLT_RELATED_OBJECTS structure that is passed to lower minifilter drivers. For more information, see <a href="ifsk.modifying_the_parameters_for_an_i_o_operation">Modifying the Parameters for an I/O Operation</a>. </p>

<p>A minifilter driver receives a pointer to an FLT_RELATED_OBJECTS structure as the <i>FltObjects</i> input parameter to the following callback routine types: </p><dl>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551107">PFLT_POST_OPERATION_CALLBACK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551109">PFLT_PRE_OPERATION_CALLBACK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551096">PFLT_INSTANCE_SETUP_CALLBACK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551095">PFLT_INSTANCE_QUERY_TEARDOWN_CALLBACK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551098">PFLT_INSTANCE_TEARDOWN_CALLBACK</a>
</p>
</dd>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551107">PFLT_POST_OPERATION_CALLBACK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551109">PFLT_PRE_OPERATION_CALLBACK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551096">PFLT_INSTANCE_SETUP_CALLBACK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551095">PFLT_INSTANCE_QUERY_TEARDOWN_CALLBACK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551098">PFLT_INSTANCE_TEARDOWN_CALLBACK</a>
</p>

<p>To retrieve pointers to a minifilter driver's contexts for the objects in an FLT_RELATED_OBJECTS structure, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542997">FltGetContexts</a>. </p>

<p>
<div class="alert"><b>Note</b>  <code>typedef CONST struct _FLT_RELATED_OBJECTS *PCFLT_RELATED_OBJECTS;</code></div>
<div> </div>
</p>

## -requirements
<table>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544638">FLT_IO_PARAMETER_BLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544812">FLT_RELATED_CONTEXTS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542997">FltGetContexts</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542047">FltDoCompletionProcessingWhenSafe</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551095">PFLT_INSTANCE_QUERY_TEARDOWN_CALLBACK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551096">PFLT_INSTANCE_SETUP_CALLBACK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551098">PFLT_INSTANCE_TEARDOWN_CALLBACK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551107">PFLT_POST_OPERATION_CALLBACK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551109">PFLT_PRE_OPERATION_CALLBACK</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FLT_RELATED_OBJECTS structure%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
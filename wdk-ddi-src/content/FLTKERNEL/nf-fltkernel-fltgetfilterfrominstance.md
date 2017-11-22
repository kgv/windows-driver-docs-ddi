---
UID: NF.fltkernel.FltGetFilterFromInstance
title: FltGetFilterFromInstance
author: windows-driver-content
description: The FltGetFilterFromInstance routine returns an opaque filter pointer for the minifilter driver that created the given instance.
old-location: ifsk\fltgetfilterfrominstance.htm
ms.assetid: 2fe73705-4b44-4c75-8677-3325b6be9250
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
req.alt-api: FltGetFilterFromInstance
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
ms.keywords: FltGetFilterFromInstance
req.iface: 
---

# FltGetFilterFromInstance function



## -description
<p>The <b>FltGetFilterFromInstance</b> routine returns an opaque filter pointer for the minifilter driver that created the given instance. </p>


## -syntax

````
NTSTATUS FltGetFilterFromInstance(
  _In_  PFLT_INSTANCE Instance,
  _Out_ PFLT_FILTER   *RetFilter
);
````


## -parameters
<dl>

### -param <i>Instance</i> [in]

<dd>
<p>Opaque instance pointer for the instance. </p>
</dd>

### -param <i>RetFilter</i> [out]

<dd>
<p>Pointer to a caller-allocated variable that receives an opaque filter pointer for the minifilter driver. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>
</dl>

## -returns
<p><b>FltGetFilterFromInstance</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value such as the following: </p><dl>
<dt><b>STATUS_FLT_DELETING_OBJECT</b></dt>
</dl><p>The minifilter driver is being torn down. This is an error code. </p>

<p> </p>

## -remarks
<p><b>FltGetFilterFromInstance</b> adds a rundown reference to the opaque filter pointer returned in the <i>RetFilter</i> parameter. When this pointer is no longer needed, the caller must release it by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff543378">FltObjectDereference</a>. Thus every successful call to <b>FltGetFilterFromInstance</b> must be matched by a subsequent call to <b>FltObjectDereference</b>. </p>

<p>To get an opaque volume pointer for the volume to which a given minifilter driver instance is attached, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543214">FltGetVolumeFromInstance</a>. </p>

<p>To enumerate all instances of a given minifilter driver, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542071">FltEnumerateInstanceInformationByFilter</a>. </p>

<p>To enumerate instances of all minifilter drivers on all volumes, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542090">FltEnumerateInstances</a>. </p>

<p><b>FltGetFilterFromInstance</b> adds a rundown reference to the opaque filter pointer returned in the <i>RetFilter</i> parameter. When this pointer is no longer needed, the caller must release it by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff543378">FltObjectDereference</a>. Thus every successful call to <b>FltGetFilterFromInstance</b> must be matched by a subsequent call to <b>FltObjectDereference</b>. </p>

<p>To get an opaque volume pointer for the volume to which a given minifilter driver instance is attached, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543214">FltGetVolumeFromInstance</a>. </p>

<p>To enumerate all instances of a given minifilter driver, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542071">FltEnumerateInstanceInformationByFilter</a>. </p>

<p>To enumerate instances of all minifilter drivers on all volumes, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542090">FltEnumerateInstances</a>. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542071">FltEnumerateInstanceInformationByFilter</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542090">FltEnumerateInstances</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543214">FltGetVolumeFromInstance</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543378">FltObjectDereference</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltGetFilterFromInstance routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
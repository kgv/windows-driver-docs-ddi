---
UID: NF.fltkernel.FltCurrentOplockH
title: FltCurrentOplockH
author: windows-driver-content
description: A minifilter driver calls the FltCurrentOplockH routine to determine whether there are any CACHE_HANDLE_LEVEL opportunistic locks (oplocks) on a file.
old-location: ifsk\fltcurrentoplockh.htm
ms.assetid: ee066013-99fb-4a43-82f9-edbad7b5a8e9
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: The FltCurrentOplockH routine is available starting with Windows 7.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltCurrentOplockH
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
ms.keywords: FltCurrentOplockH
req.iface: 
---

# FltCurrentOplockH function



## -description
<p>A minifilter driver calls the <b>FltCurrentOplockH</b> routine to determine whether there are any CACHE_HANDLE_LEVEL opportunistic locks (oplocks) on a file. </p>


## -syntax

````
BOOLEAN FltCurrentOplockH(
  _In_ POPLOCK Oplock
);
````


## -parameters
<dl>

### -param <i>Oplock</i> [in]

<dd>
<p>An opaque oplock pointer for the file. This pointer must have been initialized by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>. </p>
</dd>
</dl>

## -returns
<p><b>FltCurrentOplockH</b> returns <b>TRUE</b> if there are CACHE_HANDLE_LEVEL oplocks that are currently being held. Otherwise, it returns <b>FALSE</b>. </p>

## -remarks
<p><b>FltCurrentOplockH</b> returns <b>FALSE</b> if no CACHE_HANDLE_LEVEL opportunistic locks are currently held.</p>

<p>For more information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

<p><b>FltCurrentOplockH</b> returns <b>FALSE</b> if no CACHE_HANDLE_LEVEL opportunistic locks are currently held.</p>

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
<p>The FltCurrentOplockH routine is available starting with Windows 7. </p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545837">FsRtlCurrentOplockH</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltCurrentOplockH routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
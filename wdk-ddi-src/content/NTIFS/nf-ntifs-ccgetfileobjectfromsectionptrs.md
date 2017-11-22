---
UID: NF.ntifs.CcGetFileObjectFromSectionPtrs
title: CcGetFileObjectFromSectionPtrs
author: windows-driver-content
description: Given a pointer to the section object pointers for a cached file, the CcGetFileObjectFromSectionPtrs routine returns a pointer to the file object that the cache manager is using for the file.
old-location: ifsk\ccgetfileobjectfromsectionptrs.htm
ms.assetid: da756f88-e2c6-4bff-8390-be48902fe130
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CcGetFileObjectFromSectionPtrs
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
req.irql: 
ms.keywords: CcGetFileObjectFromSectionPtrs
req.iface: 
---

# CcGetFileObjectFromSectionPtrs function



## -description
<p>Given a pointer to the section object pointers for a cached file, the <b>CcGetFileObjectFromSectionPtrs</b> routine returns a pointer to the file object that the cache manager is using for the file.</p>


## -syntax

````
PFILE_OBJECT CcGetFileObjectFromSectionPtrs(
  _In_ PSECTION_OBJECT_POINTERS SectionObjectPointer
);
````


## -parameters
<dl>

### -param <i>SectionObjectPointer</i> [in]

<dd>
<p>Pointer to a structure containing the file object's section object pointers.</p>
</dd>
</dl>

## -returns
<p>A pointer to the file object, or <b>NULL</b> if the file is not cached or is no longer cached.</p>

## -remarks
<p>The file system is responsible for ensuring that the file object remains valid while in use. It is impossible for the cache manager to guarantee this. </p>

<p>By using <b>CcGetFileObjectFromSectionPtrs</b>, you lose some caching functionality. Instead, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff539113">CcGetFileObjectFromSectionPtrsRef</a> routine, which provides the same functionality as <b>CcGetFileObjectFromSectionPtrs</b> as well as creating a reference for the object.</p>

<p>For more information about creating mapped sections and views of memory, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563682">Sections and Views</a>. </p>

<p>The file system is responsible for ensuring that the file object remains valid while in use. It is impossible for the cache manager to guarantee this. </p>

<p>By using <b>CcGetFileObjectFromSectionPtrs</b>, you lose some caching functionality. Instead, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff539113">CcGetFileObjectFromSectionPtrsRef</a> routine, which provides the same functionality as <b>CcGetFileObjectFromSectionPtrs</b> as well as creating a reference for the object.</p>

<p>For more information about creating mapped sections and views of memory, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563682">Sections and Views</a>. </p>

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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539113">CcGetFileObjectFromSectionPtrsRef</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539188">CcPurgeCacheSection</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcGetFileObjectFromSectionPtrs routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
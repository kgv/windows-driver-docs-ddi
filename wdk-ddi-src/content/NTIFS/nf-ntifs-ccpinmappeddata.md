---
UID: NF.ntifs.CcPinMappedData
title: CcPinMappedData
author: windows-driver-content
description: The CcPinMappedData routine pins the specified byte range of a cached file.
old-location: ifsk\ccpinmappeddata.htm
ms.assetid: aa0903db-fced-4af9-bfc9-2769ed4962a1
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
req.alt-api: CcPinMappedData
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
req.irql: PASSIVE_LEVEL
ms.keywords: CcPinMappedData
req.iface: 
---

# CcPinMappedData function



## -description
<p>The <b>CcPinMappedData</b> routine pins the specified byte range of a cached file.</p>


## -syntax

````
BOOLEAN CcPinMappedData(
  _In_    PFILE_OBJECT   FileObject,
  _In_    PLARGE_INTEGER FileOffset,
  _In_    ULONG          Length,
  _In_    ULONG          Flags,
  _Inout_ PVOID          *Bcb
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>Pointer to a file object for the cached file in which a range of data is to be pinned.</p>
</dd>

### -param <i>FileOffset</i> [in]

<dd>
<p>Pointer to a variable that specifies the starting byte offset within the cached file where the desired data resides.</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>Length in bytes of the data to be pinned.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>Bitmask of flags specifying how the pinning operation is to be performed. ORed combination of one or more of the following values: </p>
<table>
<tr>
<th>Flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>PIN_WAIT</p>
</td>
<td>
<p>The caller can be put into a wait state until the data has been pinned.</p>
</td>
</tr>
<tr>
<td>
<p>PIN_EXCLUSIVE</p>
</td>
<td>
<p>The buffer control block (BCB) is to be acquired exclusively. If this flag is set, PIN_WAIT must also be set.</p>
</td>
</tr>
<tr>
<td>
<p>PIN_NO_READ</p>
</td>
<td>
<p>Only pages that are already resident in memory are to be pinned. If this flag is set, PIN_WAIT must also be set.</p>
</td>
</tr>
<tr>
<td>
<p>PIN_IF_BCB</p>
</td>
<td>
<p>The data is to be pinned only if a BCB already exists. Otherwise, the pin fails and <i>Bcb</i> is set to <b>NULL</b>.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -param <i>Bcb</i> [in, out]

<dd>
<p>On the first call this returns a pointer to a buffer control block (BCB). This pointer must be supplied as input on all subsequent calls for this buffer. </p>
</dd>
</dl>

## -returns
<p><b>CcPinMappedData</b> returns <b>TRUE</b> if the data for the cached file was pinned successfully, <b>FALSE</b> otherwise.</p>

## -remarks
<p>A successful return from <b>CcPinMappedData</b> guarantees that the data previously mapped in a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a> is pinned in the cache and data in the specified range can be safely modified. If the caller subsequently modifies the data pinned by <b>CcPinMappedData</b>, it must also call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539211">CcSetDirtyPinnedData</a> so that the modified data will eventually be written to disk.</p>

<p><b>CcPinMappedData</b> cannot pin data across view boundaries in the cache manager. The cache manager manages files in the system in 256 KB-aligned views. (The cache manager's view size is specified by the system-defined constant <b>VACB_MAPPING_GRANULARITY</b>, which is set to 256 KB in <i>ntifs.h</i>.) Pinned regions cannot span more than one 256 KB view. Therefore, the largest region that can be pinned is 256 KB, beginning at a 256 KB-aligned offset in the file. </p>

<p>Pinning a byte range in a cached file does not ensure that the pages remain resident in memory. As long as the pages are pinned, the byte range is guaranteed to stay mapped into the system cache virtual address space, but the memory manager can page out the physical pages as the system's memory demand requires. </p>

<p>If any failure occurs, <b>CcPinMappedData</b> raises a status exception for that particular failure. For example, if a pool allocation failure occurs, <b>CcPinMappedData</b> raises a <b>STATUS_INSUFFICIENT_RESOURCES</b> exception; if an I/O error occurs, <b>CcPinMappedData</b> raises the status exception of the I/O error. Therefore, to gain control if a failure occurs, the driver should wrap the call to <b>CcPinMappedData</b> in a <b>try-except</b> or <b>try-finally</b> statement.</p>

<p>To map data for a cached file, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a> routine. To cache a file, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>.</p>

<p>It is not necessary to call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539228">CcUnpinData</a> after calling <b>CcPinMappedData</b> since the pin reference is matched to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a>.</p>

<p>A successful return from <b>CcPinMappedData</b> guarantees that the data previously mapped in a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a> is pinned in the cache and data in the specified range can be safely modified. If the caller subsequently modifies the data pinned by <b>CcPinMappedData</b>, it must also call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539211">CcSetDirtyPinnedData</a> so that the modified data will eventually be written to disk.</p>

<p><b>CcPinMappedData</b> cannot pin data across view boundaries in the cache manager. The cache manager manages files in the system in 256 KB-aligned views. (The cache manager's view size is specified by the system-defined constant <b>VACB_MAPPING_GRANULARITY</b>, which is set to 256 KB in <i>ntifs.h</i>.) Pinned regions cannot span more than one 256 KB view. Therefore, the largest region that can be pinned is 256 KB, beginning at a 256 KB-aligned offset in the file. </p>

<p>Pinning a byte range in a cached file does not ensure that the pages remain resident in memory. As long as the pages are pinned, the byte range is guaranteed to stay mapped into the system cache virtual address space, but the memory manager can page out the physical pages as the system's memory demand requires. </p>

<p>If any failure occurs, <b>CcPinMappedData</b> raises a status exception for that particular failure. For example, if a pool allocation failure occurs, <b>CcPinMappedData</b> raises a <b>STATUS_INSUFFICIENT_RESOURCES</b> exception; if an I/O error occurs, <b>CcPinMappedData</b> raises the status exception of the I/O error. Therefore, to gain control if a failure occurs, the driver should wrap the call to <b>CcPinMappedData</b> in a <b>try-except</b> or <b>try-finally</b> statement.</p>

<p>To map data for a cached file, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a> routine. To cache a file, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>.</p>

<p>It is not necessary to call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539228">CcUnpinData</a> after calling <b>CcPinMappedData</b> since the pin reference is matched to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539155">CcMapData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539180">CcPinRead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539183">CcPreparePinWrite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539211">CcSetDirtyPinnedData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539228">CcUnpinData</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcPinMappedData routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
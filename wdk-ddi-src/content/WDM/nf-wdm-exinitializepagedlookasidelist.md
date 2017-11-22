---
UID: NF.wdm.ExInitializePagedLookasideList
title: ExInitializePagedLookasideList
author: windows-driver-content
description: The ExInitializePagedLookasideList routine initializes a lookaside list for pageable entries of the specified size.
old-location: kernel\exinitializepagedlookasidelist.htm
ms.assetid: 7a6b21f1-37e3-4f73-a826-4629624ac5a9
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ExInitializePagedLookasideList
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlExApcLte2, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
ms.keywords: ExInitializePagedLookasideList
req.iface: 
req.product: Windows 10 or later.
---

# ExInitializePagedLookasideList function



## -description
<p>The <b>ExInitializePagedLookasideList</b> routine initializes a lookaside list for pageable entries of the specified size.</p>


## -syntax

````
VOID ExInitializePagedLookasideList(
  _Out_    PPAGED_LOOKASIDE_LIST Lookaside,
  _In_opt_ PALLOCATE_FUNCTION    Allocate,
  _In_opt_ PFREE_FUNCTION        Free,
  _In_     ULONG                 Flags,
  _In_     SIZE_T                Size,
  _In_     ULONG                 Tag,
  _In_     USHORT                Depth
);
````


## -parameters
<dl>

### -param <i>Lookaside</i> [out]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558775">PAGED_LOOKASIDE_LIST</a> structure to initialize. The caller must use <u>nonpaged</u> system space for the structure, even though the entries in this lookaside list will be allocated from pageable memory. On 64-bit platforms, this structure must be 16-byte aligned.</p>
</dd>

### -param <i>Allocate</i> [in, optional]

<dd>
<p>A pointer to either a caller-supplied function for allocating an entry when the lookaside list is empty, or to <b>NULL</b>. If non-<b>NULL</b>, the pointer is to a function with the prototype:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>PVOID XxxAllocate(
  __in POOL_TYPE  PoolType,           // PagedPool 
  __in SIZE_T  NumberOfBytes,         // value of Size
  __in ULONG  Tag                     // value of Tag
);</pre>
</td>
</tr>
</table></span></div>
<p>If the <i>Allocate</i> parameter is <b>NULL</b>, subsequent calls to <b>ExAllocateFromPagedLookasideList</b> automatically allocate entries whenever the lookaside list is empty.</p>
</dd>

### -param <i>Free</i> [in, optional]

<dd>
<p>A pointer to either a caller-supplied function for freeing an entry whenever the lookaside list is full, or to <b>NULL</b>. If non-<b>NULL</b>, the pointer is to a function with the prototype:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>VOID XxxFree(
  __in PVOID  Buffer
);</pre>
</td>
</tr>
</table></span></div>
<p>If the <i>Free</i> parameter is <b>NULL</b>, subsequent calls to <b>ExFreeToPagedLookasideList</b> automatically release the given entry back to paged pool whenever the list is full, that is, currently holding the system-determined maximum number of entries.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>Starting in Windows 8, this parameter specifies an optional flag value to modify the default behavior of the <b>ExInitializePagedLookasideList</b> routine. Compatible flag bits include the following.</p>
<table>
<tr>
<th>Flag bit</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>POOL_NX_ALLOCATION</p>
</td>
<td>
<p>Allocate non-executable memory.</p>
</td>
</tr>
<tr>
<td>
<p>POOL_RAISE_IF_ALLOCATION_FAILURE</p>
</td>
<td>
<p>If the allocation fails, raise an exception.</p>
</td>
</tr>
</table>
<p> </p>
<p>Before Windows 8, this parameter is not used and must be zero.</p>
</dd>

### -param <i>Size</i> [in]

<dd>
<p>Specifies the size in bytes of each entry in the lookaside list. </p>
</dd>

### -param <i>Tag</i> [in]

<dd>
<p>Specifies the pool tag to use when allocating lookaside list entries. For more information about pool tags, see the <i>Tag</i> parameter of <a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a>. </p>
</dd>

### -param <i>Depth</i> [in]

<dd>
<p>Reserved. Must be zero. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>After calling <b>ExInitializePagedLookasideList</b>, blocks of the caller-specified <i>Size</i> can be allocated from and freed to the lookaside list with calls to <a href="https://msdn.microsoft.com/library/windows/hardware/ff544393">ExAllocateFromPagedLookasideList</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff544605">ExFreeToPagedLookasideList</a>, respectively. Such dynamically allocated and freed entries can be any data structure or fixed-size buffer that the caller uses while the system is running, particularly if the caller cannot predetermine how many such entries will be in use at any given moment. The layout and contents of each fixed-size entry are caller-determined.</p>

<p><b>ExInitializePagedLookasideList</b> initializes the system state to track usage of the given lookaside list, as follows:</p>

<p>Zero-initializes the counters to be maintained for entries.</p>

<p>Stores the entry points of the caller-supplied <b><i>Xxx</i>Allocate</b> and <b><i>Xxx</i>Free</b> routines, if any, or sets these entry points to <a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff544590">ExFreePool</a>, respectively.</p>

<p>Initializes a system spin lock to control allocations from and frees to the lookaside list in a multiprocessor-safe manner if necessary.</p>

<p>Stores the caller-supplied entry <i>Size</i> and list <i>Tag</i>.</p>

<p>Sets up the system-determined limits (minimum  and maximum) on the number of entries to be held in the lookaside list, which can be adjusted subsequently if system-wide demand for entries is higher or lower than anticipated.</p>

<p>Sets up the system-determined flags, which control the type of memory from which entries will be allocated subsequently.</p>

<p>The system maintains a set of all lookaside lists in use. As demand for lookaside list entries and on available paged memory varies while the system runs, the system adjusts its limits for the number of entries to be held in each paged lookaside list dynamically.</p>

<p>Drivers must always use explicitly free any lookaside lists they create before unloading. To do otherwise is a serious programming error. Use <a href="https://msdn.microsoft.com/library/windows/hardware/ff544570">ExDeletePagedLookasideList</a> to free the list.</p>

<p><b>ExInitializePagedLookasideList</b> sets up the opaque list head at the caller-supplied location but preallocates no memory for list entries. Subsequently, the initial entries are allocated dynamically as calls to <b>ExAllocateFromPagedLookasideList</b> occur, and these initial entries are held in the lookaside list as reciprocal calls to <b>ExFreeToPagedLookasideList</b> occur. Entries collect in the given lookaside list until the system-determined maximum is reached, whereupon any additional entries are returned to paged pool as they are freed. If the list becomes empty, allocate requests are satisfied by the <b><i>Xxx</i>Allocate</b> function specified at list initialization or by <b>ExAllocatePoolWithTag</b>.</p>

<p>It is more efficient to pass <b>NULL</b> pointers for the <i>Allocate</i> and <i>Free</i> parameters of <b>ExInitializePagedLookasideList</b> whenever the user of a lookaside list does nothing more than allocate and release fixed-size entries. However, any component that uses a lookaside list might supply these functions to do additional caller-determined processing, such as tracking its own dynamic memory usage by maintaining state about the number of entries it allocates and frees. </p>

<p>If the caller of <b>ExInitializePagedLookasideList</b> supplies an <b><i>Xxx</i>Allocate</b> function, that function must allocate entries for the lookaside list using the given input parameters when it calls <b>ExAllocatePoolWithTag.</b></p>

<p>Starting with Windows Vista, a similar routine, <a href="https://msdn.microsoft.com/library/windows/hardware/ff545298">ExInitializeLookasideListEx</a>, initializes a lookaside list that is described by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff554329">LOOKASIDE_LIST_EX</a> structure. Unlike the <b><i>Xxx</i>Allocate</b> and <b><i>Xxx</i>Free</b> routines for a lookaside list that uses a <b>PAGED_LOOKASIDE_LIST</b> structure, the allocation and deallocation routines for a lookaside list that uses the <b>LOOKASIDE_LIST_EX</b> structure receive a context pointer as an input parameter. These routines can use this context to store private data for the lookaside list. If your driver is intended to run only in Windows Vista and later versions of Windows, consider using <b>ExInitializeLookasideListEx</b> instead of <b>ExInitializePagedLookasideList</b>. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565416">Using Lookaside Lists</a>.</p>

<p>After calling <b>ExInitializePagedLookasideList</b>, blocks of the caller-specified <i>Size</i> can be allocated from and freed to the lookaside list with calls to <a href="https://msdn.microsoft.com/library/windows/hardware/ff544393">ExAllocateFromPagedLookasideList</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff544605">ExFreeToPagedLookasideList</a>, respectively. Such dynamically allocated and freed entries can be any data structure or fixed-size buffer that the caller uses while the system is running, particularly if the caller cannot predetermine how many such entries will be in use at any given moment. The layout and contents of each fixed-size entry are caller-determined.</p>

<p><b>ExInitializePagedLookasideList</b> initializes the system state to track usage of the given lookaside list, as follows:</p>

<p>Zero-initializes the counters to be maintained for entries.</p>

<p>Stores the entry points of the caller-supplied <b><i>Xxx</i>Allocate</b> and <b><i>Xxx</i>Free</b> routines, if any, or sets these entry points to <a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff544590">ExFreePool</a>, respectively.</p>

<p>Initializes a system spin lock to control allocations from and frees to the lookaside list in a multiprocessor-safe manner if necessary.</p>

<p>Stores the caller-supplied entry <i>Size</i> and list <i>Tag</i>.</p>

<p>Sets up the system-determined limits (minimum  and maximum) on the number of entries to be held in the lookaside list, which can be adjusted subsequently if system-wide demand for entries is higher or lower than anticipated.</p>

<p>Sets up the system-determined flags, which control the type of memory from which entries will be allocated subsequently.</p>

<p>The system maintains a set of all lookaside lists in use. As demand for lookaside list entries and on available paged memory varies while the system runs, the system adjusts its limits for the number of entries to be held in each paged lookaside list dynamically.</p>

<p>Drivers must always use explicitly free any lookaside lists they create before unloading. To do otherwise is a serious programming error. Use <a href="https://msdn.microsoft.com/library/windows/hardware/ff544570">ExDeletePagedLookasideList</a> to free the list.</p>

<p><b>ExInitializePagedLookasideList</b> sets up the opaque list head at the caller-supplied location but preallocates no memory for list entries. Subsequently, the initial entries are allocated dynamically as calls to <b>ExAllocateFromPagedLookasideList</b> occur, and these initial entries are held in the lookaside list as reciprocal calls to <b>ExFreeToPagedLookasideList</b> occur. Entries collect in the given lookaside list until the system-determined maximum is reached, whereupon any additional entries are returned to paged pool as they are freed. If the list becomes empty, allocate requests are satisfied by the <b><i>Xxx</i>Allocate</b> function specified at list initialization or by <b>ExAllocatePoolWithTag</b>.</p>

<p>It is more efficient to pass <b>NULL</b> pointers for the <i>Allocate</i> and <i>Free</i> parameters of <b>ExInitializePagedLookasideList</b> whenever the user of a lookaside list does nothing more than allocate and release fixed-size entries. However, any component that uses a lookaside list might supply these functions to do additional caller-determined processing, such as tracking its own dynamic memory usage by maintaining state about the number of entries it allocates and frees. </p>

<p>If the caller of <b>ExInitializePagedLookasideList</b> supplies an <b><i>Xxx</i>Allocate</b> function, that function must allocate entries for the lookaside list using the given input parameters when it calls <b>ExAllocatePoolWithTag.</b></p>

<p>Starting with Windows Vista, a similar routine, <a href="https://msdn.microsoft.com/library/windows/hardware/ff545298">ExInitializeLookasideListEx</a>, initializes a lookaside list that is described by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff554329">LOOKASIDE_LIST_EX</a> structure. Unlike the <b><i>Xxx</i>Allocate</b> and <b><i>Xxx</i>Free</b> routines for a lookaside list that uses a <b>PAGED_LOOKASIDE_LIST</b> structure, the allocation and deallocation routines for a lookaside list that uses the <b>LOOKASIDE_LIST_EX</b> structure receive a context pointer as an input parameter. These routines can use this context to store private data for the lookaside list. If your driver is intended to run only in Windows Vista and later versions of Windows, consider using <b>ExInitializeLookasideListEx</b> instead of <b>ExInitializePagedLookasideList</b>. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565416">Using Lookaside Lists</a>.</p>

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
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547751">IrqlExApcLte2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544393">ExAllocateFromPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544520">ExAllocatePoolWithTag</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544570">ExDeletePagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544590">ExFreePool</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544605">ExFreeToPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545298">ExInitializeLookasideListEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545301">ExInitializeNPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554329">LOOKASIDE_LIST_EX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558775">PAGED_LOOKASIDE_LIST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ExInitializePagedLookasideList routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
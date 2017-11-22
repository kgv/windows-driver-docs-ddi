---
UID: NF.wdm.ClfsAlignReservedLog
title: ClfsAlignReservedLog
author: windows-driver-content
description: The ClfsAlignReservedLog routine calculates the size of the space that must be reserved for a specified set of records. The size calculation includes the space required for headers and the space required for sector alignment.
old-location: kernel\clfsalignreservedlog.htm
ms.assetid: b79f58bb-af94-4143-9e30-6f50d85cbb3d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Server 2003 R2, Windows Vista, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ClfsAlignReservedLog
req.alt-loc: Clfs.sys,Ext-MS-Win-fs-clfs-l1-1-0.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Clfs.lib
req.dll: Clfs.sys
req.irql: <= APC_LEVEL
ms.keywords: ClfsAlignReservedLog
req.iface: 
req.product: Windows 10 or later.
---

# ClfsAlignReservedLog function



## -description
<p>The <b>ClfsAlignReservedLog</b> routine calculates the size of the space that must be reserved for a specified set of records. The size calculation includes the space required for headers and the space required for sector alignment.</p>


## -syntax

````
NTSTATUS  ClfsAlignReservedLog(
  _In_  PVOID     pvMarshalContext,
  _In_  ULONG     cRecords,
  _In_  LONGLONG  rgcbReservation[],
  _Out_ PLONGLONG pcbAlignReservation
);
````


## -parameters
<dl>

### -param <i>pvMarshalContext</i> [in]

<dd>
<p>A pointer to an opaque context that represents a marshalling area associated with a CLFS stream. The caller previously obtained this pointer by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff541520">ClfsCreateMarshallingArea</a>.</p>
</dd>

### -param <i>cRecords</i> [in]

<dd>
<p>The number of elements in the array pointed to by <i>rgcbReservation</i>.</p>
</dd>

### -param <i>rgcbReservation</i> [in]

<dd>
<p>A pointer to an array of LONGLONG-typed variables that supplies a list of record sizes (in bytes).</p>
</dd>

### -param <i>pcbAlignReservation</i> [out]

<dd>
<p>A pointer to a LONGLONG-typed variable that receives the size, in bytes, of the required reservation.</p>
</dd>
</dl>

## -returns
<p><b>ClfsAlignReservedLog</b> returns STATUS_SUCCESS if it succeeds; otherwise, it returns one of the error codes defined in Ntstatus.h. </p>

## -remarks
<p>For an explanation of CLFS concepts and terminology, see <a href="https://msdn.microsoft.com/a9685648-b08c-48ca-b020-e683068f2ea2">Common Log File System</a>. </p>

<p>For an explanation of CLFS concepts and terminology, see <a href="https://msdn.microsoft.com/a9685648-b08c-48ca-b020-e683068f2ea2">Common Log File System</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Server 2003 R2, Windows Vista, and later versions of Windows.</p>
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
<dt>Clfs.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Clfs.sys</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540782">ClfsAllocReservedLog</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ClfsAlignReservedLog routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
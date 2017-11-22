---
UID: NF.mcd.ChangerClassInitialize
title: ChangerClassInitialize
author: windows-driver-content
description: The ChangerClassInitialize routine initializes the driver.
old-location: storage\changerclassinitialize.htm
ms.assetid: b19f85f7-fe51-4539-8c36-e3c6a299faad
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: mcd.h
req.include-header: Mcd.h, Ntddchgr.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ChangerClassInitialize
req.alt-loc: Mcd.lib,Mcd.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Mcd.lib
req.dll: 
req.irql: 
ms.keywords: ChangerClassInitialize
req.iface: 
---

# ChangerClassInitialize function



## -description
<p>The <b>ChangerClassInitialize</b> routine initializes the driver. </p>


## -syntax

````
NTSTATUS ChangerClassInitialize(
  _In_ PDRIVER_OBJECT  DriverObject,
  _In_ PUNICODE_STRING RegistryPath,
  _In_ PMCD_INIT_DATA  MCDInitData
);
````


## -parameters
<dl>

### -param <i>DriverObject</i> [in]

<dd>
<p>Pointer to the changer miniclass driver object.  This is passed as a parameter to the miniclass driver's <b>DriverEntry</b> routine. The format of this object is operating system-specific and should not be interpreted by the miniclass driver. </p>
</dd>

### -param <i>RegistryPath</i> [in]

<dd>
<p>Pointer to the registry path for changer miniclass driver. This is also passed as a parameter to the miniclass driver's <b>DriverEntry</b> routine. The format of this is operating system-specific and should not be interpreted by the miniclass driver.</p>
</dd>

### -param <i>MCDInitData</i> [in]

<dd>
<p>Pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff562210">MCD_INIT_DATA</a> structure containing miniclass driver-specific information such as the entry points for the changer miniclass driver's command processing routines. </p>
</dd>
</dl>

## -returns
<p><b>ChangerClassInitialize</b> returns a value indicating the success or failure of  the driver initialization. If initialization is successful, <b>ChangerClassInitialize</b> returns STATUS_SUCCESS. Otherwise, <b>ChangerClassInitialize</b> returns an appropriate error message. Minidrivers should <i>not</i> interpret this error value, but should just return this value from their <b>DriverEntry</b> routine. </p>

## -remarks
<p><b>ChangerClassInitialize</b> is a changer class driver routine that miniclass drivers can call in Microsoft Windows XP and later operating systems.</p>

<p>Changer miniclass drivers call <b>ChangerClassInitialize</b> from within their <b>DriverEntry</b> routines to initialize the driver. <b>ChangerClassInitialize</b> performs many tasks formerly performed by the changer class driver's <b>DriverEntry</b> routine such as registering the miniclass driver's dispatch routines. It allocates a driver object extension and copies the data contained in <i>MCDInitData</i> into the driver object extension along with other initialization data such as the driver's registry path and pointers to certain changer class driver routines that are operating system-specific. </p>

<p>Changer miniclass drivers must allocate an <a href="https://msdn.microsoft.com/library/windows/hardware/ff562210">MCD_INIT_DATA</a> structure, zero the structure by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff563610">RtlZeroMemory</a>, and then assign values to the appropriate members, before passing the structure's address to <b>ChangerClassInitialize</b> by means of the <i>MCDInitData</i> parameter. </p>

<p><b>ChangerClassInitialize</b> is a changer class driver routine that miniclass drivers can call in Microsoft Windows XP and later operating systems.</p>

<p>Changer miniclass drivers call <b>ChangerClassInitialize</b> from within their <b>DriverEntry</b> routines to initialize the driver. <b>ChangerClassInitialize</b> performs many tasks formerly performed by the changer class driver's <b>DriverEntry</b> routine such as registering the miniclass driver's dispatch routines. It allocates a driver object extension and copies the data contained in <i>MCDInitData</i> into the driver object extension along with other initialization data such as the driver's registry path and pointers to certain changer class driver routines that are operating system-specific. </p>

<p>Changer miniclass drivers must allocate an <a href="https://msdn.microsoft.com/library/windows/hardware/ff562210">MCD_INIT_DATA</a> structure, zero the structure by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff563610">RtlZeroMemory</a>, and then assign values to the appropriate members, before passing the structure's address to <b>ChangerClassInitialize</b> by means of the <i>MCDInitData</i> parameter. </p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Mcd.h (include Mcd.h or Ntddchgr.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Mcd.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562210">MCD_INIT_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563610">RtlZeroMemory</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ChangerClassInitialize routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
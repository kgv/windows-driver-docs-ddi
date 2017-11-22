---
UID: NF.storport.StorPortReadRegisterUlong
title: StorPortReadRegisterUlong
author: windows-driver-content
description: The StorPortReadRegisterUlong routine reads a value from a specified register address.
old-location: storage\storportreadregisterulong.htm
ms.assetid: 308e6401-9726-4333-bde8-1aec9558c5fb
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortReadRegisterUlong
req.alt-loc: Storport.lib,Storport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Storport.lib
req.dll: 
req.irql: 
ms.keywords: StorPortReadRegisterUlong
req.iface: 
req.product: Windows 10 or later.
---

# StorPortReadRegisterUlong function



## -description
<p>The <b>StorPortReadRegisterUlong</b> routine reads a value from a specified register address. </p>


## -syntax

````
STORPORT_API ULONG StorPortReadRegisterUlong(
  _In_ PVOID  HwDeviceExtension,
  _In_ PULONG Register
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>Pointer to the hardware device extension.</p>
</dd>

### -param <i>Register</i> [in]

<dd>
<p>Pointer to the register where the data is to be read. </p>
</dd>
</dl>

## -returns
<p><b>StorPortReadRegisterUlong</b> returns an unsigned character of data read from the indicated register address. </p>

## -remarks
<p>For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564742">ScsiPortReadRegisterUlong</a>. For a buffered version of this routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff567480">StorPortReadRegisterBufferUlong</a>.</p>

<p>For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff564742">ScsiPortReadRegisterUlong</a>. For a buffered version of this routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff567480">StorPortReadRegisterBufferUlong</a>.</p>

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
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Storport.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564742">ScsiPortReadRegisterUlong</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567480">StorPortReadRegisterBufferUlong</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortReadRegisterUlong routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.irb.AtaPortReadPortBufferUlong
title: AtaPortReadPortBufferUlong
author: windows-driver-content
description: The AtaPortReadPortBufferUlong routine transfers a given number of ULONG values from the HBA to a buffer.Note  The ATA port driver and ATA miniport driver models may be altered or unavailable in the future.
old-location: storage\ataportreadportbufferulong.htm
ms.assetid: ff70685f-f3cf-49c0-bb0b-02e561feeac3
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: irb.h
req.include-header: Ata.h, Irb.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: AtaPortReadPortBufferUlong
req.alt-loc: ataport.lib,ataport.dll,pciidex.lib,pciidex.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ataport.lib; 
Pciidex.lib
req.dll: 
req.irql: 
ms.keywords: AtaPortReadPortBufferUlong
req.iface: 
---

# AtaPortReadPortBufferUlong function



## -description
<p>The <b>AtaPortReadPortBufferUlong</b> routine transfers a given number of ULONG values from the HBA to a buffer.</p>


## -syntax

````
VOID AtaPortReadPortBufferUlong(
  _In_ PULONG Port,
  _In_ PULONG Buffer,
  _In_ ULONG  Count
);
````


## -parameters
<dl>

### -param <i>Port</i> [in]

<dd>
<p>A pointer to the I/O port. The address value that is assigned to this parameter must be within the range of mapped I/O space addresses that are obtained by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff550160">AtaPortGetDeviceBase</a>.</p>
</dd>

### -param <i>Buffer</i> [in]

<dd>
<p>A pointer to the destination buffer.</p>
</dd>

### -param <i>Count</i> [in]

<dd>
<p>Specifies the number of ULONG values to read from the HBA.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks


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
<dt>Irb.h (include Ata.h or Irb.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ataport.lib; </dt>
<dt>Pciidex.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550160">AtaPortGetDeviceBase</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550175">AtaPortReadPortBufferUchar</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550180">AtaPortReadPortBufferUshort</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20AtaPortReadPortBufferUlong routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
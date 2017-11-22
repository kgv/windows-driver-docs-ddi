---
UID: NF.ntifs.FsRtlIsLeadDbcsCharacter
title: FsRtlIsLeadDbcsCharacter
author: windows-driver-content
description: The FsRtlIsLeadDbcsCharacter macro determines whether a character is a lead byte (the first byte of a character) in a double-byte character set (DBCS).
old-location: ifsk\fsrtlisleaddbcscharacter.htm
ms.assetid: 3cbae037-6205-4315-8ff7-0c67a91c4c69
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FsRtlIsLeadDbcsCharacter
req.alt-loc: ntifs.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level
ms.keywords: FsRtlIsLeadDbcsCharacter
req.iface: 
---

# FsRtlIsLeadDbcsCharacter function



## -description
<p>The <b>FsRtlIsLeadDbcsCharacter</b> macro determines whether a character is a lead byte (the first byte of a character) in a double-byte character set (DBCS). </p>


## -syntax

````
BOOLEAN FsRtlIsLeadDbcsCharacter(
  _In_ UCHAR DbcsCharacter
);
````


## -parameters
<dl>

### -param <i>DbcsCharacter</i> [in]

<dd>
<p>The character to be tested.</p>
</dd>
</dl>

## -returns
<p><b>TRUE</b> if the character is a lead byte, <b>FALSE</b> otherwise.</p>

## -remarks
<p>Lead bytes are unique to double-byte character sets. A lead byte introduces a double-byte character. Lead bytes occupy a specific range of byte values. The <b>FsRtlIsLeadDbcsCharacter</b> macro uses the system code page to check lead-byte ranges.  </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

<p>Lead bytes are unique to double-byte character sets. A lead byte introduces a double-byte character. Lead bytes occupy a specific range of byte values. The <b>FsRtlIsLeadDbcsCharacter</b> macro uses the system code page to check lead-byte ranges.  </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

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
<dt>Ntifs.h (include Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545877">FsRtlDissectDbcs</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545891">FsRtlDoesDbcsContainWildCards</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546803">FsRtlIsDbcsInExpression</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FsRtlIsLeadDbcsCharacter function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
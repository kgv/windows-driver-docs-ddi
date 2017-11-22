---
UID: NS.iscsiop._SendTargets_OUT
title: SendTargets_OUT
author: windows-driver-content
description: The SendTargets_OUT structure holds the output data for the SendTargets method.
old-location: storage\sendtargets_out.htm
ms.assetid: 82efeeb9-1167-4114-9d88-7ef66f613f80
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsiop.h
req.include-header: Iscsiop.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SendTargets_OUT
req.alt-loc: iscsiop.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: SendTargets_OUT, SendTargets_OUT, *PSendTargets_OUT
req.iface: 
---

# SendTargets_OUT structure



## -description
<p>The SendTargets_OUT structure holds the output data for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff565526">SendTargets</a> method.</p>


## -syntax

````
typedef struct _SendTargets_OUT {
  ULONG Status;
  ULONG ResponseSize;
  UCHAR Response[1];
} SendTargets_OUT, *PSendTargets_OUT;
````


## -struct-fields
<dl>

### -field <b>Status</b>

<dd>
<p>The status of the <b>SendTargets</b> method. This member will contain 0 if the SEND TARGETS operation succeeds and ISDSC_SCSI_REQUEST_FAILED if the operation fails. If the SEND TARGETS operation fails, <b>ScsiStatus</b> will contain the SCSI status of the SCSI command. SCSI status qualifiers are documented in the <i>SCSI Primary Commands</i> specification. For a list of status qualifiers, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff561568">ISCSI_STATUS_QUALIFIERS</a>.  </p>
</dd>

### -field <b>ResponseSize</b>

<dd>
<p>The size, in bytes, of the buffer at Response.</p>
</dd>

### -field <b>Response</b>

<dd>
<p>A buffer that holds the response data that the target returns. Response to SendTargets in UTF8 characters. NOTE: This field is a variable length array.</p>
</dd>
</dl>

## -remarks
<p>You must implement this method.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Iscsiop.h (include Iscsiop.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561568">ISCSI_STATUS_QUALIFIERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565526">SendTargets</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565533">SendTargets_IN</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20SendTargets_OUT structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
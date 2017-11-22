---
UID: NF.wdm.PcwCloseInstance
title: PcwCloseInstance
author: windows-driver-content
description: The PcwCloseInstance function closes the specified instance of the counter set.
old-location: devtest\pcwcloseinstance.htm
ms.assetid: a577a116-9e5e-42d3-aac0-a6b90131ad9d
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: devtest
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcwCloseInstance
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
req.irql: <=APC_LEVEL
ms.keywords: PcwCloseInstance
req.iface: 
req.product: Windows 10 or later.
---

# PcwCloseInstance function



## -description
<p>The <b>PcwCloseInstance</b> function closes the specified instance of the counter set. </p>


## -syntax

````
VOID PcwCloseInstance(
  _In_ PPCW_INSTANCE Instance
);
````


## -parameters
<dl>

### -param <i>Instance</i> [in]

<dd>
<p>A pointer to the instance of the counter set to close. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550318">PcwCreateInstance</a> function to create an instance of a registered counter set. You cannot call <b>PcwCloseInstance</b> if you have already called <a href="https://msdn.microsoft.com/library/windows/hardware/ff550326">PcwUnregister</a>. When you unregister the counter set, the instances are closed for you.</p>

<p>Use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550318">PcwCreateInstance</a> function to create an instance of a registered counter set. You cannot call <b>PcwCloseInstance</b> if you have already called <a href="https://msdn.microsoft.com/library/windows/hardware/ff550326">PcwUnregister</a>. When you unregister the counter set, the instances are closed for you.</p>

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
<p>Available in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h or Ntddk.h)</dt>
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
<p>&lt;=APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550318">PcwCreateInstance</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [devtest\devtest]:%20PcwCloseInstance function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
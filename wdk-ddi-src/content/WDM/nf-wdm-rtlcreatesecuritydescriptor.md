---
UID: NF.wdm.RtlCreateSecurityDescriptor
title: RtlCreateSecurityDescriptor
author: windows-driver-content
description: The RtlCreateSecurityDescriptor routine initializes a new absolute-format security descriptor. On return, the security descriptor is initialized with no system ACL, no discretionary ACL, no owner, no primary group, and all control flags set to zero.
old-location: kernel\rtlcreatesecuritydescriptor.htm
ms.assetid: f9e08a57-c9dd-4703-b29d-c169ba77f194
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 2000 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlCreateSecurityDescriptor
req.alt-loc: NtosKrnl.exe,Ntdll.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe (kernel mode); 
Ntdll.dll (user mode)
req.irql: PASSIVE_LEVEL
ms.keywords: RtlCreateSecurityDescriptor
req.iface: 
req.product: Windows 10 or later.
---

# RtlCreateSecurityDescriptor function



## -description
<p>The <b>RtlCreateSecurityDescriptor</b> routine initializes a new absolute-format security descriptor. On return, the security descriptor is initialized with no system ACL, no discretionary ACL, no owner, no primary group, and all control flags set to zero.</p>


## -syntax

````
NTSTATUS RtlCreateSecurityDescriptor(
  _Out_ PSECURITY_DESCRIPTOR SecurityDescriptor,
  _In_  ULONG                Revision
);
````


## -parameters
<dl>

### -param <i>SecurityDescriptor</i> [out]

<dd>
<p>Pointer to the buffer for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563689">SECURITY_DESCRIPTOR</a> to be initialized.</p>
</dd>

### -param <i>Revision</i> [in]

<dd>
<p>Specifies the revision level to assign to the security descriptor. Set this parameter to SECURITY_DESCRIPTOR_REVISION.</p>
</dd>
</dl>

## -returns
<p><b>RtlCreateSecurityDescriptor</b> can return one of the following.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The call completed successfully.</p><dl>
<dt><b>STATUS_UNKNOWN_REVISION</b></dt>
</dl><p>The caller specified an unsupported value  for <i>Revision</i>.</p>

<p> </p>

## -remarks
<p>A successful call to this routine initializes a security descriptor. The fields in this descriptor are set to initial values that indicate that there are no security constraints.</p>

<p>A successful call to this routine initializes a security descriptor. The fields in this descriptor are set to initial values that indicate that there are no security constraints.</p>

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
<p>Available in Windows 2000 and later versions of Windows.</p>
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
<dt>NtosKrnl.exe (kernel mode); </dt>
<dt>Ntdll.dll (user mode)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562025">RtlLengthSecurityDescriptor</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562781">RtlSetDaclSecurityDescriptor</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563024">RtlValidSecurityDescriptor</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563689">SECURITY_DESCRIPTOR</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlCreateSecurityDescriptor routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
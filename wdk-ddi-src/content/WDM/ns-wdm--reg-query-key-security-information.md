---
UID: NS.wdm._REG_QUERY_KEY_SECURITY_INFORMATION
title: REG_QUERY_KEY_SECURITY_INFORMATION
author: windows-driver-content
description: The REG_QUERY_KEY_SECURITY_INFORMATION structure receives security information for a registry key object.
old-location: kernel\reg_query_key_security_information.htm
ms.assetid: 8bfe793d-c902-4459-98eb-e134759efc48
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Available on Windows Vista and later versions of the Windows operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: REG_QUERY_KEY_SECURITY_INFORMATION
req.alt-loc: wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
ms.keywords: REG_QUERY_KEY_SECURITY_INFORMATION, REG_QUERY_KEY_SECURITY_INFORMATION, *PREG_QUERY_KEY_SECURITY_INFORMATION
req.iface: 
req.product: Windows 10 or later.
---

# REG_QUERY_KEY_SECURITY_INFORMATION structure



## -description
<p>The <b>REG_QUERY_KEY_SECURITY_INFORMATION</b> structure receives security information for a registry key object.</p>


## -syntax

````
typedef struct _REG_QUERY_KEY_SECURITY_INFORMATION {
  PVOID                 Object;
  PSECURITY_INFORMATION SecurityInformation;
  PSECURITY_DESCRIPTOR  SecurityDescriptor;
  PULONG                Length;
  PVOID                 CallContext;
  PVOID                 ObjectContext;
  PVOID                 Reserved;
} REG_QUERY_KEY_SECURITY_INFORMATION, *PREG_QUERY_KEY_SECURITY_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>Object</b>

<dd>
<p>A pointer to the registry key object for the key whose security information is being retrieved.</p>
</dd>

### -field <b>SecurityInformation</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff556635">SECURITY_INFORMATION</a>-typed value that identifies the type of security information that is being requested. </p>
</dd>

### -field <b>SecurityDescriptor</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563689">SECURITY_DESCRIPTOR</a> structure that receives security information for the key object. </p>
</dd>

### -field <b>Length</b>

<dd>
<p>The length, in bytes of the <b>SECURITY_DESCRIPTOR</b> structure that <b>SecurityDescriptor</b> points to.</p>
</dd>

### -field <b>CallContext</b>

<dd>
<p>Optional driver-defined context information that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine can supply. This member is defined for Windows Vista and later versions of the Windows operating system. </p>
</dd>

### -field <b>ObjectContext</b>

<dd>
<p>A pointer to driver-defined context information that the driver has associated with a registry object by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff541924">CmSetCallbackObjectContext</a>. This member is defined for Windows Vista and later versions of the Windows operating system.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>This member is reserved for future use. This member is defined for Windows Vista and later versions of the Windows operating system.</p>
</dd>
</dl>

## -remarks
<p>The system passes the <b>REG_QUERY_KEY_SECURITY_INFORMATION</b> structure to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine every time a thread attempts to query a key's security information—for example, when a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff567066">ZwQuerySecurityObject</a>.</p>

<p>For more information about registry filtering operations, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545879">Filtering Registry Calls</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available on Windows Vista and later versions of the Windows operating system.</p>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541924">CmSetCallbackObjectContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563689">SECURITY_DESCRIPTOR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556635">SECURITY_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567066">ZwQuerySecurityObject</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20REG_QUERY_KEY_SECURITY_INFORMATION structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
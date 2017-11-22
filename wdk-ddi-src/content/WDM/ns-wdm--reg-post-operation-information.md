---
UID: NS.wdm._REG_POST_OPERATION_INFORMATION
title: REG_POST_OPERATION_INFORMATION
author: windows-driver-content
description: The REG_POST_OPERATION_INFORMATION structure contains information about a completed registry operation that a RegistryCallback routine can use.
old-location: kernel\reg_post_operation_information.htm
ms.assetid: 2266e816-2060-4071-bf9f-319daefbfc50
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Available on Microsoft Windows Server 2003 and later versions of the Windows operating system, but some structure members are available only for Windows Vista and later versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: REG_POST_OPERATION_INFORMATION
req.alt-loc: Wdm.h
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
ms.keywords: REG_POST_OPERATION_INFORMATION, REG_POST_OPERATION_INFORMATION, *PREG_POST_OPERATION_INFORMATION
req.iface: 
req.product: Windows 10 or later.
---

# REG_POST_OPERATION_INFORMATION structure



## -description
<p>The <b>REG_POST_OPERATION_INFORMATION</b> structure contains information about a completed registry operation that a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine can use.</p>


## -syntax

````
typedef struct _REG_POST_OPERATION_INFORMATION {
  PVOID    Object;
  NTSTATUS Status;
  PVOID    PreInformation;
  NTSTATUS ReturnStatus;
  PVOID    CallContext;
  PVOID    ObjectContext;
  PVOID    Reserved;
} REG_POST_OPERATION_INFORMATION, *PREG_POST_OPERATION_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>Object</b>

<dd>
<p>A pointer to the registry key object for which the operation has completed. This member is valid only if the Status member of the structure is set to STATUS_SUCCESS. For more information, see <a href="http://go.microsoft.com/fwlink/p/?linkid=613134">Invalid Key Object Pointers in Registry Notifications</a>.</p>
</dd>

### -field <b>Status</b>

<dd>
<p>The NTSTATUS-typed value that the system will return for the registry operation.</p>
</dd>

### -field <b>PreInformation</b>

<dd>
<p>A pointer to the structure that contains preprocessing information for the registry operation that has completed. For example, if the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine is processing a <b>RegNtPostQueryValueKey</b> operation, the <b>PreInformation</b> member points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560991">REG_QUERY_VALUE_KEY_INFORMATION</a> structure. This member is defined for Windows Vista and later versions of the Windows operating system.</p>
</dd>

### -field <b>ReturnStatus</b>

<dd>
<p>A driver-supplied NTSTATUS-typed value. If the driver's <i>RegistryCallback</i> routine returns STATUS_CALLBACK_BYPASS, the operating system uses the <b>ReturnStatus</b> member's value as the status that it returns to the thread that initiated the registry operation. (In such cases, the operating system also copies the <b>ReturnStatus</b> member's value to the <b>Status</b> member.) Otherwise, this member is ignored. This member is defined for Windows Vista and later versions of the Windows operating system.</p>
</dd>

### -field <b>CallContext</b>

<dd>
<p>Optional driver-defined context information that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> routine can supply. This member is defined for Windows Vista and later versions of the Windows operating system.</p>
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
<p>For more information about handling post-notifications, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546907">Handling Notifications</a>.</p>

<p>For more information about registry filtering operations, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545879">Filtering Registry Calls</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available on Microsoft Windows Server 2003 and later versions of the Windows operating system, but some structure members are available only for Windows Vista and later versions.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560991">REG_QUERY_VALUE_KEY_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20REG_POST_OPERATION_INFORMATION structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
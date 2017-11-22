---
UID: NF.wdffileobject.WdfFileObjectGetInitiatorProcessId
title: WdfFileObjectGetInitiatorProcessId
author: windows-driver-content
description: The WdfFileObjectGetInitiatorProcessId function retrieves the initiator process ID that is associated with a specified framework file object.
old-location: wdf\wdffileobjectgetinitiatorprocessid.htm
ms.assetid: 59E15EAA-4934-48D9-A9E3-7CDEEAE01985
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdffileobject.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.21
req.umdf-ver: 2.0
req.alt-api: WdfFileObjectGetInitiatorProcessId
req.alt-loc: WUDFx02000.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.lib
req.dll: WUDFx02000.dll
req.irql: DISPATCH_LEVEL
ms.keywords: WdfFileObjectGetInitiatorProcessId
req.iface: 
req.product: Windows 10 or later.
---

# WdfFileObjectGetInitiatorProcessId function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfFileObjectGetInitiatorProcessId</b> function retrieves the initiator process ID that is associated with a specified framework file object.</p>


## -syntax

````
ULONG WdfFileObjectGetInitiatorProcessId(
  _In_ WDFFILEOBJECT FileObject
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>A handle to a framework file object.</p>
</dd>
</dl>

## -returns
<p>Returns the initiator process identifier associated with the file, if any exists. Otherwise, the function returns zero.</p>

## -remarks
<p>Starting in Windows 8, a system component may issue a create on behalf of an application. The driver can call <b>WdfFileObjectGetInitiatorProcessId</b> to determine which process the create operation is ultimately intended for.</p>

<p><b>WdfFileObjectGetInitiatorProcessId</b> returns zero if no initiator process is associated with the create operation.</p>

<p>Starting in Windows 8, a system component may issue a create on behalf of an application. The driver can call <b>WdfFileObjectGetInitiatorProcessId</b> to determine which process the create operation is ultimately intended for.</p>

<p><b>WdfFileObjectGetInitiatorProcessId</b> returns zero if no initiator process is associated with the create operation.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.21</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdffileobject.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx02000.dll</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/4D23A651-7231-40CE-B9C2-4382D4E7F683">IWDFDevice3::GetInitiatorProcessId</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn265617">WdfRequestGetRequestorProcessId</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfFileObjectGetInitiatorProcessId function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
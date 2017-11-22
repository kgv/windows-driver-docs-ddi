---
UID: NF.wdm.IoInvalidateDeviceState
title: IoInvalidateDeviceState
author: windows-driver-content
description: The IoInvalidateDeviceState routine notifies the PnP manager that some aspect of the PnP state of a device has changed.
old-location: kernel\ioinvalidatedevicestate.htm
ms.assetid: ca27e8d3-80ee-467c-9c88-19770cd86d94
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoInvalidateDeviceState
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
req.irql: <= DISPATCH_LEVEL
ms.keywords: IoInvalidateDeviceState
req.iface: 
req.product: Windows 10 or later.
---

# IoInvalidateDeviceState function



## -description
<p>The <b>IoInvalidateDeviceState</b> routine notifies the PnP manager that some aspect of the PnP state of a device has changed. </p>


## -syntax

````
VOID IoInvalidateDeviceState(
  _In_ PDEVICE_OBJECT PhysicalDeviceObject
);
````


## -parameters
<dl>

### -param <i>PhysicalDeviceObject</i> [in]

<dd>
<p>Pointer to the PDO for the device. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Drivers call this routine to indicate that something has changed with respect to one of the following aspects of a device's PnP state:</p><dl>
<dd>
<p>PNP_DEVICE_DISABLED</p>
</dd>
<dd>
<p>PNP_DEVICE_DONT_DISPLAY_IN_UI</p>
</dd>
<dd>
<p>PNP_DEVICE_FAILED</p>
</dd>
<dd>
<p>PNP_DEVICE_NOT_DISABLEABLE</p>
</dd>
<dd>
<p>PNP_DEVICE_REMOVED</p>
</dd>
<dd>
<p>PNP_DEVICE_RESOURCE_REQUIREMENTS_CHANGED</p>
</dd>
</dl><p>PNP_DEVICE_DISABLED</p>

<p>PNP_DEVICE_DONT_DISPLAY_IN_UI</p>

<p>PNP_DEVICE_FAILED</p>

<p>PNP_DEVICE_NOT_DISABLEABLE</p>

<p>PNP_DEVICE_REMOVED</p>

<p>PNP_DEVICE_RESOURCE_REQUIREMENTS_CHANGED</p>

<p>For descriptions of the preceding constants, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff559618">PNP_DEVICE_STATE</a>.</p>

<p>In response to this routine, the PnP manager sends an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551698">IRP_MN_QUERY_PNP_DEVICE_STATE</a> request to the device stack, to determine the current PnP state of the device.</p>

<p>Drivers call this routine to indicate that something has changed with respect to one of the following aspects of a device's PnP state:</p><dl>
<dd>
<p>PNP_DEVICE_DISABLED</p>
</dd>
<dd>
<p>PNP_DEVICE_DONT_DISPLAY_IN_UI</p>
</dd>
<dd>
<p>PNP_DEVICE_FAILED</p>
</dd>
<dd>
<p>PNP_DEVICE_NOT_DISABLEABLE</p>
</dd>
<dd>
<p>PNP_DEVICE_REMOVED</p>
</dd>
<dd>
<p>PNP_DEVICE_RESOURCE_REQUIREMENTS_CHANGED</p>
</dd>
</dl><p>PNP_DEVICE_DISABLED</p>

<p>PNP_DEVICE_DONT_DISPLAY_IN_UI</p>

<p>PNP_DEVICE_FAILED</p>

<p>PNP_DEVICE_NOT_DISABLEABLE</p>

<p>PNP_DEVICE_REMOVED</p>

<p>PNP_DEVICE_RESOURCE_REQUIREMENTS_CHANGED</p>

<p>For descriptions of the preceding constants, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff559618">PNP_DEVICE_STATE</a>.</p>

<p>In response to this routine, the PnP manager sends an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551698">IRP_MN_QUERY_PNP_DEVICE_STATE</a> request to the device stack, to determine the current PnP state of the device.</p>

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
<p>Available starting with Windows 2000.</p>
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
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551698">IRP_MN_QUERY_PNP_DEVICE_STATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559618">PNP_DEVICE_STATE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoInvalidateDeviceState routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.portcls.PcRegisterAdapterPowerManagement
title: PcRegisterAdapterPowerManagement
author: windows-driver-content
description: The PcRegisterAdapterPowerManagement function registers the adapter's power-management interface with the PortCls system driver.
old-location: audio\pcregisteradapterpowermanagement.htm
ms.assetid: a9e2537d-4d67-4495-b391-55f885b7041a
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: audio
req.header: portcls.h
req.include-header: Portcls.h
req.target-type: Universal
req.target-min-winverclnt: Available starting in Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcRegisterAdapterPowerManagement
req.alt-loc: Portcls.lib,Portcls.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Portcls.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: PcRegisterAdapterPowerManagement
req.iface: 
---

# PcRegisterAdapterPowerManagement function



## -description
<p>The <b>PcRegisterAdapterPowerManagement</b> function registers the adapter's power-management interface with the PortCls system driver.</p>


## -syntax

````
NTSTATUS PcRegisterAdapterPowerManagement(
  _In_ PUNKNOWN pUnknown,
  _In_ PVOID    pvContext1
);
````


## -parameters
<dl>

### -param <i>pUnknown</i> [in]

<dd>
<p>Pointer to an adapter driver object's <a href="com.iunknown">IUnknown</a> interface. The PortCls system driver queries this object for its <a href="https://msdn.microsoft.com/library/windows/hardware/ff536485">IAdapterPowerManagement</a> interface.</p>
</dd>

### -param <i>pvContext1</i> [in]

<dd>
<p>Pointer to the adapter's <a href="wdkgloss.f#wdkgloss.functional_device_object__fdo_#wdkgloss.functional_device_object__fdo_"><i>functional device object (FDO)</i></a>. This parameter is a pointer to a system structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> but is cast to type PVOID.</p>
</dd>
</dl>

## -returns
<p><b>PcRegisterAdapterPowerManagement</b> returns STATUS_SUCCESS if the call was successful. Otherwise, it returns an appropriate error code.</p>

## -remarks


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
<p>Available starting in Windows 2000. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Portcls.h (include Portcls.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Portcls.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536485">IAdapterPowerManagement</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PcRegisterAdapterPowerManagement function%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
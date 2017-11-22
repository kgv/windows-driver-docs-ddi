---
UID: NF.ucxcontroller.UCX_CONTROLLER_CONFIG_SET_PCI_INFO
title: UCX_CONTROLLER_CONFIG_SET_PCI_INFO
author: windows-driver-content
description: Initializes a UCX_CONTROLLER_CONFIG structure with the specified values for the controller with PCI as the parent bus type.
old-location: buses\_ucx_controller_config_set_pci_info.htm
ms.assetid: 493B8E5B-D2CC-453E-8202-69337FAC85ED
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: usbref
req.header: ucxcontroller.h
req.include-header: Ucxclass.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: UCX_CONTROLLER_CONFIG_SET_PCI_INFO
req.alt-loc: Ucxcontroller.h
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
ms.keywords: UCX_CONTROLLER_CONFIG_SET_PCI_INFO
req.iface: 
req.product: Windows 10 or later.
---

# UCX_CONTROLLER_CONFIG_SET_PCI_INFO function



## -description
<p>Initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/mt188057">UCX_CONTROLLER_CONFIG</a> structure with the specified values for the controller with PCI as the parent bus type.</p>


## -syntax

````
__inline
void UCX_CONTROLLER_CONFIG_SET_PCI_INFO(
  _In_ PUCX_CONTROLLER_CONFIG Config,
  _In_ ULONG                  VendorId,
  _In_ ULONG                  DeviceId,
  _In_ USHORT                 RevisionId,
  _In_ ULONG                  BusNumber,
  _In_ ULONG                  DeviceNumber,
  _In_ ULONG                  FunctionNumber
);
````


## -parameters
<dl>

### -param <i>Config</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt188057">UCX_CONTROLLER_CONFIG</a> structure to initialize.</p>
</dd>

### -param <i>VendorId</i> [in]

<dd>
<p>Specifies the vendor identifier for the device as assigned by the PCI SIG.</p>
</dd>

### -param <i>DeviceId</i> [in]

<dd>
<p>Specifies the device identifier assigned by the manufacturer. </p>
</dd>

### -param <i>RevisionId</i> [in]

<dd>
<p>Specifies the revision level of the device described by the <b>DeviceID</b> member.</p>
</dd>

### -param <i>BusNumber</i> [in]

<dd>
<p>Specifies the bus number that identifies the bus instance that a device instance is attached to.</p>
</dd>

### -param <i>DeviceNumber</i> [in]

<dd>
<p>Specifies the device number that is assigned to the logical PCI slot. </p>
</dd>

### -param <i>FunctionNumber</i> [in]

<dd>
<p>Specifies the specific function on the device that is located in the logical PCI slot. </p>
</dd>
</dl>

## -returns
<p>This function does not return a value.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum support</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ucxcontroller.h (include Ucxclass.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt188033">UcxControllerCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt188057">UCX_CONTROLLER_CONFIG</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20UCX_CONTROLLER_CONFIG_SET_PCI_INFO function%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
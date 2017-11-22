---
UID: NF.wdm.IoGetDeviceNumaNode
title: IoGetDeviceNumaNode
author: windows-driver-content
description: The IoGetDeviceNumaNode routine gets the node number of a device.
old-location: kernel\iogetdevicenumanode.htm
ms.assetid: a36e9d57-c820-43db-a6e0-e935bffca254
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoGetDeviceNumaNode
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: IoGetDeviceNumaNode
req.iface: 
req.product: Windows 10 or later.
---

# IoGetDeviceNumaNode function



## -description
<p>The <b>IoGetDeviceNumaNode</b> routine gets the node number of a device. </p>


## -syntax

````
NTSTATUS IoGetDeviceNumaNode(
  _In_  PDEVICE_OBJECT Pdo,
  _Out_ PUSHORT        NodeNumber
);
````


## -parameters
<dl>

### -param <i>Pdo</i> [in]

<dd>
<p>A pointer to a physical device object (PDO). This parameter points to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure that represents a physical device. </p>
</dd>

### -param <i>NodeNumber</i> [out]

<dd>
<p>A pointer to a location into which the routine writes the node number, if the node number is known. </p>
</dd>
</dl>

## -returns
<p><b>IoGetDeviceNumaNode</b> returns STATUS_SUCCESS if the call is successful. Possible error return values include the following:</p><dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl><p>The node number of this device is unknown. </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The <i>Pdo</i> parameter is <b>NULL</b> or does not point to a valid device object. </p>

<p> </p>

## -remarks
<p>In a non-uniform memory access (NUMA) multiprocessor architecture, a node is a collection of processors that share fast access to a region of memory. Memory access is non-uniform because a processor can access the memory in its node faster than it can access the memory in other nodes.</p>

<p>A device (for example, a network controller or storage controller) that is connected to a particular node can access the memory in this node faster than it can access the memory in other nodes. The <i>Pdo</i> parameter points to a PDO that represents the bus connection between the device and the node.</p>

<p>If a NUMA multiprocessor system contains <i>n</i> nodes, the nodes are numbered from 0 to <i>n</i>-1. To obtain the highest node number, call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553020">KeQueryHighestNodeNumber</a> routine.</p>

<p>After the system is initialized, the node count remains fixed while the system continues to run. This count might include memory-only nodes, which are nodes that contain memory but no active logical processors. A node in which all the logical processors are inactive is effectively a memory-only node until the first processor in the node starts to run. Do not assume that the node that a device is connected to contains active processors.</p>

<p>If a system does not have a NUMA architecture, the routine writes zero to the location that the <i>NodeNumber</i> parameter points to. An example of non-NUMA architecture is a symmetric multiprocessor system (SMP). </p>

<p>In a non-uniform memory access (NUMA) multiprocessor architecture, a node is a collection of processors that share fast access to a region of memory. Memory access is non-uniform because a processor can access the memory in its node faster than it can access the memory in other nodes.</p>

<p>A device (for example, a network controller or storage controller) that is connected to a particular node can access the memory in this node faster than it can access the memory in other nodes. The <i>Pdo</i> parameter points to a PDO that represents the bus connection between the device and the node.</p>

<p>If a NUMA multiprocessor system contains <i>n</i> nodes, the nodes are numbered from 0 to <i>n</i>-1. To obtain the highest node number, call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553020">KeQueryHighestNodeNumber</a> routine.</p>

<p>After the system is initialized, the node count remains fixed while the system continues to run. This count might include memory-only nodes, which are nodes that contain memory but no active logical processors. A node in which all the logical processors are inactive is effectively a memory-only node until the first processor in the node starts to run. Do not assume that the node that a device is connected to contains active processors.</p>

<p>If a system does not have a NUMA architecture, the routine writes zero to the location that the <i>NodeNumber</i> parameter points to. An example of non-NUMA architecture is a symmetric multiprocessor system (SMP). </p>

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
<p>Available in Windows 7 and later versions of the Windows operating systems.</p>
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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553020">KeQueryHighestNodeNumber</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoGetDeviceNumaNode routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.fwpsk.FwpsReferenceNetBufferList0
title: FwpsReferenceNetBufferList0
author: windows-driver-content
description: The FwpsReferenceNetBufferList0 function increments the reference count for a NET_BUFFER_LIST structure.Note  FwpsReferenceNetBufferList0 is a specific version of FwpsReferenceNetBufferList.
old-location: netvista\fwpsreferencenetbufferlist0.htm
ms.assetid: ff387b49-fecb-41d0-aac5-0a83eb8835d6
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FwpsReferenceNetBufferList0
req.alt-loc: fwpkclnt.lib,fwpkclnt.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fwpkclnt.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: FwpsReferenceNetBufferList0
req.iface: 
---

# FwpsReferenceNetBufferList0 function



## -description
<p>The 
  <b>FwpsReferenceNetBufferList0</b> function increments the reference count for a 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure.</p>


## -syntax

````
void NTAPI FwpsReferenceNetBufferList0(
  _Inout_ NET_BUFFER_LIST *netBufferList,
  _In_    BOOLEAN         intendToModify
);
````


## -parameters
<dl>

### -param <i>netBufferList</i> [in, out]

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure for which the
     reference count is being incremented.</p>
</dd>

### -param <i>intendToModify</i> [in]

<dd>
<p>A value that indicates whether a callout intends to modify the cloned network buffer list, whose
     parent is pointed to by the 
     <i>netBufferList</i> parameter, after the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a> function has returned. If <b>TRUE</b>,
     the callout intends to modify the cloned net buffer list after 
     <i>classifyFn</i> has returned (an out-of-band modification). Otherwise, set to <b>FALSE</b>.</p>
</dd>
</dl>

## -returns
<p>None.</p>

## -remarks
<p>A callout driver calls the 
    <b>FwpsReferenceNetBufferList0</b> function to increment the reference count for a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure such that the network
    buffer list remains valid outside of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a> function.</p>

<p>For example, when a callout driver performs packet reassembly, it increments the reference count for
    each of the received NET_BUFFER_LIST structures that describe the packet fragments that make up an
    individual packet. This allows the new NET_BUFFER_LIST structure that describes the reassembled packet to
    safely reference the memory descriptor lists (MDLs) pointed to by the NET_BUFFER_LIST structures that describe the packet
    fragments. After the callout driver has injected the new NET_BUFFER_LIST structure into the network
    stack, it decrements the reference count for each of the NET_BUFFER_LIST structures that describe the
    packet fragments from its packet injection completion routine.</p>

<p>A callout driver must call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff551159">FwpsDereferenceNetBufferList0</a> function for the NET_BUFFER_LIST structure after the callout driver
    has finished referencing the structure.</p>

<p>A callout driver must not hold referenced packets indefinitely. A referenced packet can interfere
     with power management operations on an idle computer.</p>

<p>The intended use for referenced packets in WFP is to get clarification from a user-mode application
     or other relatively fast operation. The callout driver must not hold referenced packets while, for
     example, waiting for user input, web service clearance, or any other
     operation that might take an arbitrary amount of time.</p>

<p>If the callout driver must wait for a potentially lengthy operation, it should make a deep copy of
     the packet using 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff551135">FwpsAllocateNetBufferAndNetBufferList0</a> and block and absorb the original packet.</p>

<p>Callout drivers should always return held packets as quickly as possible.</p>

<p>A callout driver calls the 
    <b>FwpsReferenceNetBufferList0</b> function to increment the reference count for a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure such that the network
    buffer list remains valid outside of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a> function.</p>

<p>For example, when a callout driver performs packet reassembly, it increments the reference count for
    each of the received NET_BUFFER_LIST structures that describe the packet fragments that make up an
    individual packet. This allows the new NET_BUFFER_LIST structure that describes the reassembled packet to
    safely reference the memory descriptor lists (MDLs) pointed to by the NET_BUFFER_LIST structures that describe the packet
    fragments. After the callout driver has injected the new NET_BUFFER_LIST structure into the network
    stack, it decrements the reference count for each of the NET_BUFFER_LIST structures that describe the
    packet fragments from its packet injection completion routine.</p>

<p>A callout driver must call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff551159">FwpsDereferenceNetBufferList0</a> function for the NET_BUFFER_LIST structure after the callout driver
    has finished referencing the structure.</p>

<p>A callout driver must not hold referenced packets indefinitely. A referenced packet can interfere
     with power management operations on an idle computer.</p>

<p>The intended use for referenced packets in WFP is to get clarification from a user-mode application
     or other relatively fast operation. The callout driver must not hold referenced packets while, for
     example, waiting for user input, web service clearance, or any other
     operation that might take an arbitrary amount of time.</p>

<p>If the callout driver must wait for a potentially lengthy operation, it should make a deep copy of
     the packet using 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff551135">FwpsAllocateNetBufferAndNetBufferList0</a> and block and absorb the original packet.</p>

<p>Callout drivers should always return held packets as quickly as possible.</p>

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
<p>Available starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fwpsk.h (include Fwpsk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Fwpkclnt.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e327fe9d-9425-4cc3-9552-88e9c4c3bdbe">
   FwpsDereferenceNetBufferList0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FwpsReferenceNetBufferList0 function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
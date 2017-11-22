---
UID: NC.ndis.PROTOCOL_STATUS_EX
title: PROTOCOL_STATUS_EX
author: windows-driver-content
description: The ProtocolStatusEx function indicates status-changes from underlying connectionless drivers or NDIS.Note  You must declare the function by using the PROTOCOL_STATUS_EX type.
old-location: netvista\protocolstatusex.htm
ms.assetid: 5bc5a24f-5f28-4502-8776-b1cf15fd8283
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ProtocolStatusEx
req.alt-loc: Ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: RxNameCacheInitialize
req.iface: 
---

# PROTOCOL_STATUS_EX callback



## -description
<p>The 
  <i>ProtocolStatusEx</i> function indicates status-changes from underlying connectionless drivers or
  NDIS.</p>


## -prototype

````
PROTOCOL_STATUS_EX ProtocolStatusEx;

VOID ProtocolStatusEx(
  _In_ NDIS_HANDLE             ProtocolBindingContext,
  _In_ PNDIS_STATUS_INDICATION StatusIndication
)
{ ... }
````


## -parameters
<dl>

### -param <i>ProtocolBindingContext</i> [in]

<dd>
<p>A handle to a context area that the protocol driver allocated. The protocol driver maintains the
     per-binding context information in this context area. The driver supplied this handle to NDIS when the
     driver called the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a> function.</p>
</dd>

### -param <i>StatusIndication</i> [in]

<dd>
<p>A pointer to an 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff567373">NDIS_STATUS_INDICATION</a> structure
     that contains the status information.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A call to 
    <i>ProtocolStatusEx</i> notifies the protocol driver about changes in status of an underlying driver.</p>

<p>To determine link status, use the status indications from underlying drivers instead of OID queries.
    These status indications will improve system performance and avoid possible race conditions.</p>

<p>NDIS calls the 
    <i>ProtocolStatusEx</i> function of all bound protocol drivers when an underlying driver is resetting a
    NIC. First NDIS specifies the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff567420">NDIS_STATUS_RESET_START</a> code and
    later, when the reset operation is complete, NDIS specifies the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff567419">NDIS_STATUS_RESET_END</a> code.</p>

<p>NDIS will not accept send requests and OID requests for a miniport adapter while a reset operation is
    in progress, the NDIS_STATUS_RESET_START notification warns bound protocol drivers to stop such requests
    on the affected binding until they receive the corresponding NDIS_STATUS_RESET_END notification.</p>

<p>NDIS calls 
    <i>ProtocolStatusEx</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>ProtocolStatusEx</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>ProtocolStatusEx</i> function that is named "MyStatusEx", use the <b>PROTOCOL_STATUS_EX</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>PROTOCOL_STATUS_EX</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>PROTOCOL_STATUS_EX</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p>A call to 
    <i>ProtocolStatusEx</i> notifies the protocol driver about changes in status of an underlying driver.</p>

<p>To determine link status, use the status indications from underlying drivers instead of OID queries.
    These status indications will improve system performance and avoid possible race conditions.</p>

<p>NDIS calls the 
    <i>ProtocolStatusEx</i> function of all bound protocol drivers when an underlying driver is resetting a
    NIC. First NDIS specifies the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff567420">NDIS_STATUS_RESET_START</a> code and
    later, when the reset operation is complete, NDIS specifies the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff567419">NDIS_STATUS_RESET_END</a> code.</p>

<p>NDIS will not accept send requests and OID requests for a miniport adapter while a reset operation is
    in progress, the NDIS_STATUS_RESET_START notification warns bound protocol drivers to stop such requests
    on the affected binding until they receive the corresponding NDIS_STATUS_RESET_END notification.</p>

<p>NDIS calls 
    <i>ProtocolStatusEx</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>ProtocolStatusEx</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>ProtocolStatusEx</i> function that is named "MyStatusEx", use the <b>PROTOCOL_STATUS_EX</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>PROTOCOL_STATUS_EX</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>PROTOCOL_STATUS_EX</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
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
<a href="https://msdn.microsoft.com/15f82163-a1b5-4cef-a53e-8a97adb2cd92">MiniportResetEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567373">NDIS_STATUS_INDICATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567419">NDIS_STATUS_RESET_END</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567420">NDIS_STATUS_RESET_START</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20PROTOCOL_STATUS_EX callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
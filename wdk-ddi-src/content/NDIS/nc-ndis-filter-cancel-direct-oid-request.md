---
UID: NC.ndis.FILTER_CANCEL_DIRECT_OID_REQUEST
title: FILTER_CANCEL_DIRECT_OID_REQUEST
author: windows-driver-content
description: NDIS calls a filter driver's FilterCancelDirectOidRequest function to cancel a direct OID request.Note  You must declare the function by using the FILTER_CANCEL_DIRECT_OID_REQUEST type.
old-location: netvista\filtercanceldirectoidrequest.htm
ms.assetid: 3587c5dc-3b4c-4aab-8c2d-cc9988373a56
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.1 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FilterCancelDirectOidRequest
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

# FILTER_CANCEL_DIRECT_OID_REQUEST callback



## -description
<p>NDIS calls a filter driver's 
  <i>FilterCancelDirectOidRequest</i> function to cancel a direct OID request.</p>


## -prototype

````
FILTER_CANCEL_DIRECT_OID_REQUEST FilterCancelDirectOidRequest;

VOID FilterCancelDirectOidRequest(
  _In_ NDIS_HANDLE FilterModuleContext,
  _In_ PVOID       RequestId
)
{ ... }
````


## -parameters
<dl>

### -param <i>FilterModuleContext</i> [in]

<dd>
<p>A handle to the context area for the filter module that is the target of this request. The filter
     driver created and initialized this context area in the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a> function.</p>
</dd>

### -param <i>RequestId</i> [in]

<dd>
<p>A cancellation identifier for the request. This identifier specifies the direct OID requests that
     match this value in the 
     <b>RequestId</b> member of the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><i>FilterCancelDirectOidRequest</i> is an optional function. If a filter driver does
    not use direct OID requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="https://msdn.microsoft.com/14381de2-36d9-4ec8-9d4e-7af3e6d8ecf3">
    NdisFRegisterFilterDriver</a> function.</p>

<p>When NDIS calls 
    <i>FilterCancelDirectOidRequest</i>, the filter driver should attempt to call 
    <a href="https://msdn.microsoft.com/b6b4d4f4-63d5-496c-9082-f2e8d1a174ec">
    NdisFDirectOidRequestComplete</a> function as soon as possible.</p>

<p>If a filter driver does not queue direct OID requests, the driver is not required to provide a 
    <i>FilterCancelDirectOidRequest</i> function. If the filter driver does not specify a 
    <i>FilterCancelDirectOidRequest</i> entry point, NDIS calls the cancel OID request
    function of the underlying driver.</p>

<p>NDIS calls the 
    <i>FilterCancelDirectOidRequest</i> function when the originator of the request
    cancels therequest.</p>

<p>If the request processing is still not complete in a filter driver, the driver calls the 
    <b>NdisFDirectOidRequestComplete</b> function with the status set to NDIS_STATUS_REQUEST_ABORTED.</p>

<p>If the filter driver forwarded the request to an underlying driver and the processing is still not
    complete, the filter driver calls the 
    <a href="https://msdn.microsoft.com/05cbeca1-7420-41c6-8868-980b265523db">
    NdisFCancelDirectOidRequest</a> function with the 
    <i>OidRequest</i> parameter set to the value that it sent to the underlying
    driver.</p>

<p>NDIS calls 
    <i>FilterCancelDirectOidRequest</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>FilterCancelDirectOidRequest</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>FilterCancelDirectOidRequest</i> function that is named "MyCancelDirectOidRequest", use the <b>FILTER_CANCEL_DIRECT_OID_REQUEST</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>FILTER_CANCEL_DIRECT_OID_REQUEST</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_CANCEL_DIRECT_OID_REQUEST</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p><i>FilterCancelDirectOidRequest</i> is an optional function. If a filter driver does
    not use direct OID requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="https://msdn.microsoft.com/14381de2-36d9-4ec8-9d4e-7af3e6d8ecf3">
    NdisFRegisterFilterDriver</a> function.</p>

<p>When NDIS calls 
    <i>FilterCancelDirectOidRequest</i>, the filter driver should attempt to call 
    <a href="https://msdn.microsoft.com/b6b4d4f4-63d5-496c-9082-f2e8d1a174ec">
    NdisFDirectOidRequestComplete</a> function as soon as possible.</p>

<p>If a filter driver does not queue direct OID requests, the driver is not required to provide a 
    <i>FilterCancelDirectOidRequest</i> function. If the filter driver does not specify a 
    <i>FilterCancelDirectOidRequest</i> entry point, NDIS calls the cancel OID request
    function of the underlying driver.</p>

<p>NDIS calls the 
    <i>FilterCancelDirectOidRequest</i> function when the originator of the request
    cancels therequest.</p>

<p>If the request processing is still not complete in a filter driver, the driver calls the 
    <b>NdisFDirectOidRequestComplete</b> function with the status set to NDIS_STATUS_REQUEST_ABORTED.</p>

<p>If the filter driver forwarded the request to an underlying driver and the processing is still not
    complete, the filter driver calls the 
    <a href="https://msdn.microsoft.com/05cbeca1-7420-41c6-8868-980b265523db">
    NdisFCancelDirectOidRequest</a> function with the 
    <i>OidRequest</i> parameter set to the value that it sent to the underlying
    driver.</p>

<p>NDIS calls 
    <i>FilterCancelDirectOidRequest</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>FilterCancelDirectOidRequest</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>FilterCancelDirectOidRequest</i> function that is named "MyCancelDirectOidRequest", use the <b>FILTER_CANCEL_DIRECT_OID_REQUEST</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>FILTER_CANCEL_DIRECT_OID_REQUEST</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_CANCEL_DIRECT_OID_REQUEST</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.1 and later.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561788">NdisFCancelDirectOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b6b4d4f4-63d5-496c-9082-f2e8d1a174ec">
   NdisFDirectOidRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562608">NdisFRegisterFilterDriver</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FILTER_CANCEL_DIRECT_OID_REQUEST callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
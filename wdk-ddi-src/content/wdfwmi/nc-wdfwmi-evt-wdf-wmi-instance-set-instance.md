---
UID: NC.wdfwmi.EVT_WDF_WMI_INSTANCE_SET_INSTANCE
title: EVT_WDF_WMI_INSTANCE_SET_INSTANCE
author: windows-driver-content
description: A driver's EvtWmiInstanceSetInstance callback function sets all of a WMI data provider's instance data to values that a WMI client supplies.
old-location: wdf\evtwmiinstancesetinstance.htm
ms.assetid: defd33c5-90ae-40c9-9123-7c3de2c77f35
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfwmi.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: EvtWmiInstanceSetInstance
req.alt-loc: WdfWMI.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfVerifierKeBugCheck
req.iface: 
req.product: Windows 10 or later.
---

# EVT_WDF_WMI_INSTANCE_SET_INSTANCE callback



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>A driver's <i>EvtWmiInstanceSetInstance</i> callback function sets all of a WMI data provider's instance data to values that a WMI client supplies.</p>


## -prototype

````
EVT_WDF_WMI_INSTANCE_SET_INSTANCE EvtWmiInstanceSetInstance;

NTSTATUS EvtWmiInstanceSetInstance(
  _In_ WDFWMIINSTANCE WmiInstance,
  _In_ ULONG          InBufferSize,
  _In_ PVOID          InBuffer
)
{ ... }
````


## -parameters
<dl>

### -param <i>WmiInstance</i> [in]

<dd>
<p>A handle to a WMI instance object.</p>
</dd>

### -param <i>InBufferSize</i> [in]

<dd>
<p>The size, in bytes, of the input buffer that <i>InBuffer</i> points to.</p>
</dd>

### -param <i>InBuffer</i> [in]

<dd>
<p>A pointer to the input buffer.</p>
</dd>
</dl>

## -returns
<p>The <i>EvtWmiInstanceSetInstance</i> callback function must return STATUS_SUCCESS if the operation succeeds. Otherwise, this function must return a status value for which <a href="https://msdn.microsoft.com/fe823930-e3ff-4c95-a640-bb6470c95d1d">NT_SUCCESS</a>(<i>status</i>) equals <b>FALSE</b>. If the input buffer that the <i>InBuffer</i> parameter points to is too small to contain all of the data that the driver expects, the callback function must return STATUS_WMI_SET_FAILURE.</p>

## -remarks
<p>To register an <i>EvtWmiInstanceSetInstance</i> callback function, your driver must place the function's address in a <a href="https://msdn.microsoft.com/library/windows/hardware/ff553058">WDF_WMI_INSTANCE_CONFIG</a> structure before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff551178">WdfWmiInstanceCreate</a>. </p>

<p>The framework does not synchronize calls to a driver's WMI event callback functions with each other or with any of the driver's other event callback functions. If an <i>EvtWmiInstanceSetInstance</i> callback function's data is dynamic and shared with other callback functions, your driver can use the framework's <a href="wdf.using_framework_locks">wait locks or spin locks</a> to synchronize access to the data.</p>

<p>For more information about the <i>EvtWmiInstanceSetInstance</i> callback function, see <a href="wdf.supporting_wmi_in_kmdf_drivers">Supporting WMI in Framework-Based Drivers</a>.</p>

<p>To define an <i>EvtWmiInstanceSetInstance</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtWmiInstanceSetInstance</i> callback function that is named <i>MyWmiInstanceSetInstance</i>, use the <b>EVT_WDF_WMI_INSTANCE_SET_INSTANCE</b> type as shown in this code example:</p>

<p>To define an <i>EvtWmiInstanceSetInstance</i> callback function that is named <b>MyWmiInstanceSetInstance</b>, you must first provide a function declaration that SDV and other verification tools require, as follows:</p>

<p>Then, implement your callback function as follows:</p>

<p>The <b>EVT_WDF_WMI_INSTANCE_SET_INSTANCE</b> function type is defined in the WdfWMI.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDF_WMI_INSTANCE_SET_INSTANCE</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.</p>

<p>To register an <i>EvtWmiInstanceSetInstance</i> callback function, your driver must place the function's address in a <a href="https://msdn.microsoft.com/library/windows/hardware/ff553058">WDF_WMI_INSTANCE_CONFIG</a> structure before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff551178">WdfWmiInstanceCreate</a>. </p>

<p>The framework does not synchronize calls to a driver's WMI event callback functions with each other or with any of the driver's other event callback functions. If an <i>EvtWmiInstanceSetInstance</i> callback function's data is dynamic and shared with other callback functions, your driver can use the framework's <a href="wdf.using_framework_locks">wait locks or spin locks</a> to synchronize access to the data.</p>

<p>For more information about the <i>EvtWmiInstanceSetInstance</i> callback function, see <a href="wdf.supporting_wmi_in_kmdf_drivers">Supporting WMI in Framework-Based Drivers</a>.</p>

<p>To define an <i>EvtWmiInstanceSetInstance</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtWmiInstanceSetInstance</i> callback function that is named <i>MyWmiInstanceSetInstance</i>, use the <b>EVT_WDF_WMI_INSTANCE_SET_INSTANCE</b> type as shown in this code example:</p>

<p>To define an <i>EvtWmiInstanceSetInstance</i> callback function that is named <b>MyWmiInstanceSetInstance</b>, you must first provide a function declaration that SDV and other verification tools require, as follows:</p>

<p>Then, implement your callback function as follows:</p>

<p>The <b>EVT_WDF_WMI_INSTANCE_SET_INSTANCE</b> function type is defined in the WdfWMI.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDF_WMI_INSTANCE_SET_INSTANCE</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.</p>

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
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>WdfWMI.h (include Wdf.h)</dt>
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
<a href="https://msdn.microsoft.com/13eed838-2943-4bb4-915f-6a84f0f95851">EvtWmiInstanceQueryInstance</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3011d92c-b12b-4240-8a4e-aa039ab8e053">EvtWmiInstanceSetItem</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b14de1d7-0df2-46d1-a3bd-c23f33d3ed75">EvtWmiInstanceExecuteMethod</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/89b48747-d3aa-48c7-825c-94545f378f07">EvtWmiProviderFunctionControl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553058">WDF_WMI_INSTANCE_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551178">WdfWmiInstanceCreate</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20EVT_WDF_WMI_INSTANCE_SET_INSTANCE callback function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NC.wdfchildlist.EVT_WDF_CHILD_LIST_CREATE_DEVICE
title: EVT_WDF_CHILD_LIST_CREATE_DEVICE
author: windows-driver-content
description: A bus driver'sEvtChildListCreateDevice event callback function creates a framework device object for a new device that has been dynamically enumerated.
old-location: wdf\evtchildlistcreatedevice.htm
ms.assetid: 296fbe06-1680-43a8-b5c3-1a1faa19c6c3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfchildlist.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: EvtChildListCreateDevice
req.alt-loc: WdfChildlist.h
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
ms.keywords: WDBGEXTS_THREAD_OS_INFO, WDBGEXTS_THREAD_OS_INFO, *PWDBGEXTS_THREAD_OS_INFO
req.iface: 
req.product: Windows 10 or later.
---

# EVT_WDF_CHILD_LIST_CREATE_DEVICE callback



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>A bus driver's<i>EvtChildListCreateDevice</i> event callback function creates a framework device object for a new device that has been dynamically enumerated.</p>


## -prototype

````
EVT_WDF_CHILD_LIST_CREATE_DEVICE EvtChildListCreateDevice;

NTSTATUS EvtChildListCreateDevice(
  _In_ WDFCHILDLIST                                 ChildList,
  _In_ PWDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER IdentificationDescription,
  _In_ PWDFDEVICE_INIT                              ChildInit
)
{ ... }
````


## -parameters
<dl>

### -param <i>ChildList</i> [in]

<dd>
<p>A handle to the framework child-list object that the driver specified when it called <a href="https://msdn.microsoft.com/library/windows/hardware/ff545591">WdfChildListAddOrUpdateChildDescriptionAsPresent</a>.</p>
</dd>

### -param <i>IdentificationDescription</i> [in]

<dd>
<p>A pointer to a copy of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551223">WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER</a> structure that the driver specified when it called <a href="https://msdn.microsoft.com/library/windows/hardware/ff545591">WdfChildListAddOrUpdateChildDescriptionAsPresent</a>.</p>
</dd>

### -param <i>ChildInit</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure.</p>
</dd>
</dl>

## -returns
<p>The <i>EvtChildListCreateDevice</i> callback function must return STATUS_SUCCESS, or another status value for which <a href="https://msdn.microsoft.com/fe823930-e3ff-4c95-a640-bb6470c95d1d">NT_SUCCESS</a>(<i>status</i>) equals <b>TRUE</b>, if the operation succeeds. Otherwise, this function must return a status value for which NT_SUCCESS(<i>status</i>) equals <b>FALSE</b>.</p>

<p>If the operation failed but you think your driver should try again later, and if the driver's <i>EvtChildListCreateDevice</i> callback function has not called <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, the driver can return STATUS_RETRY. As a result, the framework calls the <i>EvtChildListCreateDevice</i> callback function again later. If your driver returns STATUS_RETRY more than a few times, the framework will stop calling the callback function for the failing device.</p>

## -remarks
<p>If a bus driver is using <a href="wdf.dynamic_enumeration">dynamic enumeration</a>, it can register an <i>EvtChildListCreateDevice</i> callback function by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff547258">WdfFdoInitSetDefaultChildListConfig</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545615">WdfChildListCreate</a>.</p>

<p>After a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff545591">WdfChildListAddOrUpdateChildDescriptionAsPresent</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545667">WdfChildListUpdateAllChildDescriptionsAsPresent</a>, the framework calls the driver's <i>EvtChildListCreateDevice</i> callback function. The callback function must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a> to create a framework device object (a PDO).</p>

<p>Before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, the driver must call framework-supplied functions that initialize the WDFDEVICE_INIT structure. For more information about these functions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a>.</p>

<p>For more information about calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, see <a href="wdf.creating_a_framework_device_object">Creating a Framework Device Object</a>.</p>

<p>For more information about dynamic enumeration, see <a href="wdf.enumerating_the_devices_on_a_bus">Enumerating the Devices on a Bus</a>.</p>

<p>To define an <i>EvtChildListCreateDevice</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtChildListCreateDevice</i> callback function that is named <i>MyChildListCreateDevice</i>, use the <b>EVT_WDF_CHILD_LIST_CREATE_DEVICE</b> type as shown in this code example:</p>

<p>Then, implement your callback function as follows:</p>

<p>The <b>EVT_WDF_CHILD_LIST_CREATE_DEVICE</b> function type is defined in the WdfChildlist.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDF_CHILD_LIST_CREATE_DEVICE</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.</p>

<p>If a bus driver is using <a href="wdf.dynamic_enumeration">dynamic enumeration</a>, it can register an <i>EvtChildListCreateDevice</i> callback function by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff547258">WdfFdoInitSetDefaultChildListConfig</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545615">WdfChildListCreate</a>.</p>

<p>After a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff545591">WdfChildListAddOrUpdateChildDescriptionAsPresent</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545667">WdfChildListUpdateAllChildDescriptionsAsPresent</a>, the framework calls the driver's <i>EvtChildListCreateDevice</i> callback function. The callback function must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a> to create a framework device object (a PDO).</p>

<p>Before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, the driver must call framework-supplied functions that initialize the WDFDEVICE_INIT structure. For more information about these functions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a>.</p>

<p>For more information about calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, see <a href="wdf.creating_a_framework_device_object">Creating a Framework Device Object</a>.</p>

<p>For more information about dynamic enumeration, see <a href="wdf.enumerating_the_devices_on_a_bus">Enumerating the Devices on a Bus</a>.</p>

<p>To define an <i>EvtChildListCreateDevice</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtChildListCreateDevice</i> callback function that is named <i>MyChildListCreateDevice</i>, use the <b>EVT_WDF_CHILD_LIST_CREATE_DEVICE</b> type as shown in this code example:</p>

<p>Then, implement your callback function as follows:</p>

<p>The <b>EVT_WDF_CHILD_LIST_CREATE_DEVICE</b> function type is defined in the WdfChildlist.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDF_CHILD_LIST_CREATE_DEVICE</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.</p>

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
<dt>WdfChildlist.h (include Wdf.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551223">WDF_CHILD_IDENTIFICATION_DESCRIPTION_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545591">WdfChildListAddOrUpdateChildDescriptionAsPresent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545615">WdfChildListCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545667">WdfChildListUpdateAllChildDescriptionsAsPresent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547258">WdfFdoInitSetDefaultChildListConfig</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20EVT_WDF_CHILD_LIST_CREATE_DEVICE callback function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.wdm.EtwWrite
title: EtwWrite
author: windows-driver-content
description: The EtwWrite function is a tracing function for publishing events in your kernel-mode driver code.
old-location: devtest\etwwrite.htm
ms.assetid: b9d4f6da-694d-4737-9cbe-3666e693c0a2
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: devtest
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: EtwWrite
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
req.irql: Any level (See Comments section.)
ms.keywords: EtwWrite
req.iface: 
req.product: Windows 10 or later.
---

# EtwWrite function



## -description
<p>The <b>EtwWrite</b> function is a tracing function for publishing events in your kernel-mode driver code. </p>


## -syntax

````
NTSTATUS EtwWrite(
  _In_     REGHANDLE              RegHandle,
  _In_     PCEVENT_DESCRIPTOR     EventDescriptor,
  _In_opt_ LPCGUID                ActivityId,
  _In_     ULONG                  UserDataCount,
  _In_opt_ PEVENT_DATA_DESCRIPTOR UserData
);
````


## -parameters
<dl>

### -param <i>RegHandle</i> [in]

<dd>
<p>A pointer to the event provider registration handle, which is returned by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff545603">EtwRegister</a> function if the event provider registration is successful.</p>
</dd>

### -param <i>EventDescriptor</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/cfe84b3d-fed2-4624-9899-8451e5b39de0">EVENT_DESCRIPTOR</a> structure. </p>
</dd>

### -param <i>ActivityId</i> [in, optional]

<dd>
<p>The identifier that indicates the activity associated with the event. The <i>ActivityID</i> provides a way to group related events and is used in end-to-end tracing. </p>
</dd>

### -param <i>UserDataCount</i> [in]

<dd>
<p>The number of EVENT_DATA_DESCRIPTOR structures in <i>UserData</i>.</p>
</dd>

### -param <i>UserData</i> [in, optional]

<dd>
<p>A pointer to the array of EVENT_DATA_DESCRIPTOR structures. </p>
</dd>
</dl>

## -returns
<p>If the event was successfully published, <b>EtwWrite</b> returns STATUS_SUCCESS.</p>

<p>If the pointer to the event provider registration handle is invalid, <b>EtwWrite</b> returns STATUS_INVALID_HANDLE. The event provider must be registered before <b>EtwWrite</b> is called. <b>EtwWrite</b> can also return STATUS_INVALID_HANDLE if it is unable to log the event.

</p>

<p>If the number of EVENT_DATA_DESCRIPTOR structures specified in <i>UserDataCount</i> is greater than the maximum allowed (128), <b>EtwWrite</b> returns STATUS_INVALID_PARAMETER.</p>

<p>If <i>ActivityID</i> is specified, but there is insufficient memory available to log the data associated with the event, <b>EtwWrite</b> returns STATUS_NO_MEMORY.

</p>

<p>If the provider is not enabled for any session, <b>EtwWrite</b> returns STATUS_SUCCESS and the events are not logged.



</p>

<p>Events can be lost for several reasons; for example, if the event rate is too high or if the event size is greater than the buffer size. In these cases, the <b>EventsLost</b> counter, a member of the EVENT_TRACE_PROPERTIES structure for the corresponding logger, is updated with the number of events that were not recorded.

</p>

## -remarks
<p>The <b>EtwWrite</b> function is the kernel-mode equivalent of the user-mode <b>EventWrite</b> function. To ensure that there is a consumer for the event you are publishing, you can precede the call to <b>EtwWrite</b> with a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff545590">EtwEventEnabled</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545595">EtwProviderEnabled</a>. </p>

<p>Before you can call <b>EtwWrite</b> function to publish an event, you must register the provider with <b>EtwRegister</b>. No tracing calls should be made that fall outside of the code bounded by the <b>EtwRegister</b> and <b>EtwUnregister</b> functions. For the best performance, you can call the <b>EtwRegister</b> function in your <b>DriverEntry</b> routine and the <b>EtwUnregister</b> function in your <b>DriverUnload</b> routine.</p>

<p>If you are using the optional <i>UserData</i> parameter in the <b>EtwWrite</b> function to log additional event data, you can use the <b>EventDataDescCreate</b> macro to simplify the creation of the EVENT_DATA_DESCRIPTOR structures. The following example uses the <b>EventDataDescCreate</b> macro to initialize EVENT_DATA_DESCRIPTOR structures with  the name of the device and its status. The <b>EventDataDescCreate</b> macro stores pointers to the data (that is, it does not store copies of the data). The pointers must remain valid until the call to <b>EtwWrite</b> returns.</p>

<p>You can call <b>EtwWrite</b> at any IRQL. However, when IRQL is greater than APC_LEVEL, any data passed to the <b>EtwWrite</b>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn144773">EtwWriteEx</a>, <b>EtwWriteString</b>, <b>EtwWriteTransfer</b> functions must not be pageable. That is, any kernel-mode routine that is running at IRQL greater than APC_LEVEL cannot access pageable memory.  Data passed to the <b>EtwWrite</b>, <b>EtwWriteEx</b>, <b>EtwWriteString</b>, and <b>EtwWriteTransfer</b> functions must reside in system-space memory, regardless of what the IRQL is.</p>

<p>The <b>EtwWrite</b> function is the kernel-mode equivalent of the user-mode <b>EventWrite</b> function. To ensure that there is a consumer for the event you are publishing, you can precede the call to <b>EtwWrite</b> with a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff545590">EtwEventEnabled</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545595">EtwProviderEnabled</a>. </p>

<p>Before you can call <b>EtwWrite</b> function to publish an event, you must register the provider with <b>EtwRegister</b>. No tracing calls should be made that fall outside of the code bounded by the <b>EtwRegister</b> and <b>EtwUnregister</b> functions. For the best performance, you can call the <b>EtwRegister</b> function in your <b>DriverEntry</b> routine and the <b>EtwUnregister</b> function in your <b>DriverUnload</b> routine.</p>

<p>If you are using the optional <i>UserData</i> parameter in the <b>EtwWrite</b> function to log additional event data, you can use the <b>EventDataDescCreate</b> macro to simplify the creation of the EVENT_DATA_DESCRIPTOR structures. The following example uses the <b>EventDataDescCreate</b> macro to initialize EVENT_DATA_DESCRIPTOR structures with  the name of the device and its status. The <b>EventDataDescCreate</b> macro stores pointers to the data (that is, it does not store copies of the data). The pointers must remain valid until the call to <b>EtwWrite</b> returns.</p>

<p>You can call <b>EtwWrite</b> at any IRQL. However, when IRQL is greater than APC_LEVEL, any data passed to the <b>EtwWrite</b>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn144773">EtwWriteEx</a>, <b>EtwWriteString</b>, <b>EtwWriteTransfer</b> functions must not be pageable. That is, any kernel-mode routine that is running at IRQL greater than APC_LEVEL cannot access pageable memory.  Data passed to the <b>EtwWrite</b>, <b>EtwWriteEx</b>, <b>EtwWriteString</b>, and <b>EtwWriteTransfer</b> functions must reside in system-space memory, regardless of what the IRQL is.</p>

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
<p>Available in Windows Vista and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h or Ntddk.h)</dt>
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
<p>Any level (See Comments section.)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn144773">EtwWriteEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545642">EtwWriteTransfer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545637">EtwWriteString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545590">EtwEventEnabled</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545595">EtwProviderEnabled</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545603">EtwRegister</a>
</dt>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=70404">EventDataDescCreate</a></dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545613">EtwUnregister</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [devtest\devtest]:%20EtwWrite function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
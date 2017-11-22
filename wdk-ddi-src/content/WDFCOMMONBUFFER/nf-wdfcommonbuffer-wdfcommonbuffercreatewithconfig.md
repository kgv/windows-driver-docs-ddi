---
UID: NF.wdfcommonbuffer.WdfCommonBufferCreateWithConfig
title: WdfCommonBufferCreateWithConfig
author: windows-driver-content
description: The WdfCommonBufferCreateWithConfig method creates a memory buffer that both the driver and a direct memory access (DMA) device can access simultaneously, and the method also specifies buffer configuration information.
old-location: wdf\wdfcommonbuffercreatewithconfig.htm
ms.assetid: 3ed8b7df-9c7d-44de-a49d-10221acf71e3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfcommonbuffer.h
req.include-header: WdfCommonBuffer.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.1
req.umdf-ver: 
req.alt-api: WdfCommonBufferCreateWithConfig
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfCommonBufferCreateWithConfig
req.iface: 
req.product: Windows 10 or later.
---

# WdfCommonBufferCreateWithConfig function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfCommonBufferCreateWithConfig</b> method creates a memory buffer that both the driver and a direct memory access (DMA) device can access simultaneously, and the method also specifies buffer configuration information.</p>


## -syntax

````
NTSTATUS WdfCommonBufferCreateWithConfig(
  _In_     WDFDMAENABLER             DmaEnabler,
  _In_     size_t                    Length,
  _In_     PWDF_COMMON_BUFFER_CONFIG Config,
  _In_opt_ PWDF_OBJECT_ATTRIBUTES    Attributes,
  _Out_    WDFCOMMONBUFFER           *CommonBuffer
);
````


## -parameters
<dl>

### -param <i>DmaEnabler</i> [in]

<dd>
<p>A handle to a DMA enabler object that the driver obtained by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff546983">WdfDmaEnablerCreate</a>.  </p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>The desired size, in bytes, of the new buffer.</p>
</dd>

### -param <i>Config</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff551244">WDF_COMMON_BUFFER_CONFIG</a> structure that contains configuration information about the buffer.</p>
</dd>

### -param <i>Attributes</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure that specifies object attributes for the common buffer object. (The structure's <b>ParentObject</b> member must be <b>NULL</b>.) This parameter is optional and can be WDF_NO_OBJECT_ATTRIBUTES. </p>
</dd>

### -param <i>CommonBuffer</i> [out]

<dd>
<p>A pointer to a WDFCOMMONBUFFER-typed variable that receives a handle to a common buffer object.</p>
</dd>
</dl>

## -returns
<p><b>WdfCommonBufferCreateWithConfig</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method might return one of the following values:</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The driver supplied an invalid parameter.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>The framework could not allocate a common buffer object, or the system could not allocate a buffer.</p>

<p> </p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>The <b>WdfCommonBufferCreateWithConfig</b> method allocates memory and maps it so that both the driver and a device can access it simultaneously for DMA operations. </p>

<p>Additionally, <b>WdfCommonBufferCreateWithConfig</b> enables your driver to specify a buffer alignment requirement for the buffer. The buffer alignment requirement overrides the buffer alignment requirement that the driver specified when it called <a href="https://msdn.microsoft.com/library/windows/hardware/ff546861">WdfDeviceSetAlignmentRequirement</a>. Your driver can use <b>WdfCommonBufferCreateWithConfig</b>, instead of <a href="https://msdn.microsoft.com/library/windows/hardware/ff545800">WdfCommonBufferCreate</a>, if you want the driver to create a buffer that has a different alignment requirement than the one that <b>WdfDeviceSetAlignmentRequirement</b> specified.</p>

<p>After your driver calls <b>WdfCommonBufferCreateWithConfig</b>, the driver must:</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff545820">WdfCommonBufferGetAlignedVirtualAddress</a> to obtain the buffer's virtual address, which the driver can use.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff545814">WdfCommonBufferGetAlignedLogicalAddress</a> to obtain the buffer's logical address, which the device can use.</p>

<p>A driver typically calls <b>WdfCommonBufferCreateWithConfig</b> from within its <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function. </p>

<p>The operating system determines whether to enable cached memory in the common buffer that is to be allocated. That decision is based on the processor architecture and device bus.</p>

<p>
On computers with x86-based, x64-based, and Itanium-based processors, cached memory is enabled.
On computers with ARM or ARM 64-based processors, the operating system does not automatically enable cached memory for all devices. The system relies on the ACPI_CCA method for each device to determine whether the device is cache-coherent.</p>

<p>For more information about common buffers, see <a href="wdf.using_common_buffers">Using Common Buffers</a>
</p>

<p>The following code example initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff551244">WDF_COMMON_BUFFER_CONFIG</a> structure and then creates a 10-byte buffer that is aligned on a 32-byte boundary.</p>

<p>The <b>WdfCommonBufferCreateWithConfig</b> method allocates memory and maps it so that both the driver and a device can access it simultaneously for DMA operations. </p>

<p>Additionally, <b>WdfCommonBufferCreateWithConfig</b> enables your driver to specify a buffer alignment requirement for the buffer. The buffer alignment requirement overrides the buffer alignment requirement that the driver specified when it called <a href="https://msdn.microsoft.com/library/windows/hardware/ff546861">WdfDeviceSetAlignmentRequirement</a>. Your driver can use <b>WdfCommonBufferCreateWithConfig</b>, instead of <a href="https://msdn.microsoft.com/library/windows/hardware/ff545800">WdfCommonBufferCreate</a>, if you want the driver to create a buffer that has a different alignment requirement than the one that <b>WdfDeviceSetAlignmentRequirement</b> specified.</p>

<p>After your driver calls <b>WdfCommonBufferCreateWithConfig</b>, the driver must:</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff545820">WdfCommonBufferGetAlignedVirtualAddress</a> to obtain the buffer's virtual address, which the driver can use.</p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff545814">WdfCommonBufferGetAlignedLogicalAddress</a> to obtain the buffer's logical address, which the device can use.</p>

<p>A driver typically calls <b>WdfCommonBufferCreateWithConfig</b> from within its <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function. </p>

<p>The operating system determines whether to enable cached memory in the common buffer that is to be allocated. That decision is based on the processor architecture and device bus.</p>

<p>
On computers with x86-based, x64-based, and Itanium-based processors, cached memory is enabled.
On computers with ARM or ARM 64-based processors, the operating system does not automatically enable cached memory for all devices. The system relies on the ACPI_CCA method for each device to determine whether the device is cache-coherent.</p>

<p>For more information about common buffers, see <a href="wdf.using_common_buffers">Using Common Buffers</a>
</p>

<p>The following code example initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff551244">WDF_COMMON_BUFFER_CONFIG</a> structure and then creates a 10-byte buffer that is aligned on a 32-byte boundary.</p>

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
<p>1.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfcommonbuffer.h (include WdfCommonBuffer.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (see <a href="wdf.framework_library_versioning">Framework Library Versioning</a>.)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551244">WDF_COMMON_BUFFER_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545800">WdfCommonBufferCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545814">WdfCommonBufferGetAlignedLogicalAddress</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545820">WdfCommonBufferGetAlignedVirtualAddress</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546861">WdfDeviceSetAlignmentRequirement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546983">WdfDmaEnablerCreate</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfCommonBufferCreateWithConfig method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
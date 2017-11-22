---
UID: NF.hidpi.HidP_GetScaledUsageValue
title: HidP_GetScaledUsageValue
author: windows-driver-content
description: The HidP_GetScaledUsageValue routine returns the signed and scaled result of a HID control value extracted from a HID report.
old-location: hid\hidp_getscaledusagevalue.htm
ms.assetid: 0af1a3f2-b933-4232-865c-cccca53fd32e
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: hid
req.header: hidpi.h
req.include-header: Hidpi.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 2000 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HidP_GetScaledUsageValue
req.alt-loc: Hidparse.lib,Hidparse.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hidparse.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: HidP_GetScaledUsageValue
req.iface: 
---

# HidP_GetScaledUsageValue function



## -description
<p>The <b>HidP_GetScaledUsageValue</b> routine returns the signed and scaled result of a HID control value extracted from a HID report.</p>


## -syntax

````
NTSTATUS __stdcall HidP_GetScaledUsageValue(
  _In_  HIDP_REPORT_TYPE     ReportType,
  _In_  USAGE                UsagePage,
  _In_  USHORT               LinkCollection,
  _In_  USAGE                Usage,
  _Out_ PLONG                UsageValue,
  _In_  PHIDP_PREPARSED_DATA PreparsedData,
  _In_  PCHAR                Report,
  _In_  ULONG                ReportLength
);
````


## -parameters
<dl>

### -param <i>ReportType</i> [in]

<dd>
<p>Specifies a <b>HIDP_REPORT_TYPE</b> enumerator value that identifies the type of HID report that contains the <a href="https://msdn.microsoft.com/84fed314-3554-4291-b51c-734d874a4bab">HID usage</a> value.</p>
</dd>

### -param <i>UsagePage</i> [in]

<dd>
<p>Specifies the usage page of the value to extract.</p>
</dd>

### -param <i>LinkCollection</i> [in]

<dd>
<p>Specifies the link collection identifier of the value to extract. A LinkCollection value of zero identifies the top-level collection.</p>
</dd>

### -param <i>Usage</i> [in]

<dd>
<p>Specifies the usage of the value to extract.</p>
</dd>

### -param <i>UsageValue</i> [out]

<dd>
<p>Pointer to the buffer in which the routine returns the signed and scaled value.</p>
</dd>

### -param <i>PreparsedData</i> [in]

<dd>
<p>Pointer to the <a href="NULL">preparsed data</a> of the <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a> that generated the report located at <i>Report</i>.</p>
</dd>

### -param <i>Report</i> [in]

<dd>
<p>Pointer to the report that contains the usage.</p>
</dd>

### -param <i>ReportLength</i> [in]

<dd>
<p>Specifies the length, in bytes, of the report located at <i>Report</i>.</p>
</dd>
</dl>

## -returns
<p><b>HidP_GetScaledUsageValue</b> returns one of the following status values:</p><dl>
<dt><b>HIDP_STATUS_SUCCESS</b></dt>
</dl><p>The routine successfully returned the value.</p><dl>
<dt><b>HIDP_STATUS_INVALID_REPORT_TYPE</b></dt>
</dl><p>The specified report type is not valid.</p><dl>
<dt><b>HIDP_STATUS_INVALID_REPORT_LENGTH</b></dt>
</dl><p>The specified report length is not valid</p><dl>
<dt><b>HIDP_STATUS_BAD_LOG_PHY_VALUES</b></dt>
</dl><p>The collection returned an illegal logical or physical value. To extract the value returned by the collection, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539748">HidP_GetUsageValue</a>.</p><dl>
<dt><b>HIDP_STATUS_NULL</b></dt>
</dl><p>The current state of the scaled value from the collection is less than the logical minimum or is greater than the logical maximum, and the scaled value has a <b>NULL</b> state.</p><dl>
<dt><b>HIDP_STATUS_VALUE_OUT_OF_RANGE</b></dt>
</dl><p>The current state of the scaled value data from the collection is less than the logical minimum or is greater than the logical maximum.</p><dl>
<dt><b>HIDP_STATUS_USAGE_NOT_FOUND</b></dt>
</dl><p>The specified usage, usage page, or link collection cannot be found in any report supported by the specified top-level collection.</p><dl>
<dt><b>HIDP_STATUS_INCOMPATIBLE_REPORT_ID</b></dt>
</dl><p>The specified value is not contained in the specified report, but is contained in another report supported by the specified top-level collection.</p>

<p> </p>

## -remarks
<p>The caller-allocated buffers supplied at <i>PreparsedData</i>, <i>UsageValue</i>, and<i> Report </i>must be allocated from nonpaged pool.</p>

<p>User-mode applications and kernel-mode drivers must use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539750">HidP_GetUsageValueArray</a> to extract data for a <a href="hid.value_capability_arrays#usage_value_array#usage_value_array">usage value array</a>.</p>

<p>If the routine returns status HIDP_STATUS_BAD_LOG_PHY_VALUES, an application or driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539748">HidP_GetUsageValue</a> to extract the raw usage data.</p>

<p>For more information, see <a href="NULL">HID Collections</a>. </p>

<p>The caller-allocated buffers supplied at <i>PreparsedData</i>, <i>UsageValue</i>, and<i> Report </i>must be allocated from nonpaged pool.</p>

<p>User-mode applications and kernel-mode drivers must use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539750">HidP_GetUsageValueArray</a> to extract data for a <a href="hid.value_capability_arrays#usage_value_array#usage_value_array">usage value array</a>.</p>

<p>If the routine returns status HIDP_STATUS_BAD_LOG_PHY_VALUES, an application or driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539748">HidP_GetUsageValue</a> to extract the raw usage data.</p>

<p>For more information, see <a href="NULL">HID Collections</a>. </p>

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
<p>Available in Windows 2000 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hidpi.h (include Hidpi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Hidparse.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543586">_HIDP_PREPARSED_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539748">HidP_GetUsageValue</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539750">HidP_GetUsageValueArray</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20HidP_GetScaledUsageValue routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
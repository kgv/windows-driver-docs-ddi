---
UID: NS.ntifs._WIM_PROVIDER_ADD_OVERLAY_INPUT
title: WIM_PROVIDER_ADD_OVERLAY_INPUT
author: windows-driver-content
description: A new Windows Image File (WIM) data source is added to the WIM provider with the WIM_PROVIDER_ADD_OVERLAY_INPUT structure.
old-location: ifsk\wim_provider_add_overlay_input.htm
ms.assetid: 75C95941-367D-4A7F-A121-AF2BF9EFE28E
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h, Fltkernel.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows 8.1 Update.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WIM_PROVIDER_ADD_OVERLAY_INPUT
req.alt-loc: ntifs.h
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
ms.keywords: WIM_PROVIDER_ADD_OVERLAY_INPUT, WIM_PROVIDER_ADD_OVERLAY_INPUT, *PWIM_PROVIDER_ADD_OVERLAY_INPUT
req.iface: 
---

# WIM_PROVIDER_ADD_OVERLAY_INPUT structure



## -description
<p>A new Windows Image File (WIM) data source is added to the WIM provider with the <b>WIM_PROVIDER_ADD_OVERLAY_INPUT</b> structure.</p>


## -syntax

````
typedef struct _WIM_PROVIDER_ADD_OVERLAY_INPUT {
  ULONG WimType;
  ULONG WimIndex;
  ULONG WimFileNameOffset;
  ULONG WimFileNameLength;
} WIM_PROVIDER_ADD_OVERLAY_INPUT, *PWIM_PROVIDER_ADD_OVERLAY_INPUT;
````


## -struct-fields
<dl>

### -field <b>WimType</b>

<dd>
<p>The type of WIM file set as a backing source. The WIM file type is set to one of the following values.</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%"><a id="_WIM_BOOT_OS_WIM"></a><a id="_wim_boot_os_wim"></a><dl>

### -field <b> WIM_BOOT_OS_WIM</b>

</dl>
</td>
<td width="60%">
<p>The WIM file contains Windows system files.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="_WIM_BOOT_NOT_OS_WIM"></a><a id="_wim_boot_not_os_wim"></a><dl>

### -field <b> WIM_BOOT_NOT_OS_WIM</b>

</dl>
</td>
<td width="60%">
<p>The WIM file contains non-operating system files.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>WimIndex</b>

<dd>
<p>The index of the image in the WIM file whose filename is specified at <b>WimFileNameOffset</b>.</p>
</dd>

### -field <b>WimFileNameOffset</b>

<dd>
<p>The offset, in bytes, from the beginning of this structure of the file name for the WIM file to add as a backing source. The file name is a string of <b>WCHAR</b> character values.</p>
</dd>

### -field <b>WimFileNameLength</b>

<dd>
<p>The length, in bytes, of the file name at found at  <b>WimFileNameOffset</b>.</p>
</dd>
</dl>

## -remarks
<p>The WIM file name is included immediately following <b>WIM_PROVIDER_ADD_OVERLAY_INPUT</b> in the system buffer for a <a href="https://msdn.microsoft.com/library/windows/hardware/dn632437">FSCTL_ADD_OVERLAY</a> control request. The <b>WimFileNameOffset</b> member is set to <b>sizeof</b>(WIM_PROVIDER_ADD_OVERLAY_INPUT).</p>

<p>The WIM file name includes a terminating NULL character. <b>WimFileNameLength</b> contains the length of the file name excluding the terminating NULL.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8.1 Update.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h or Fltkernel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn632437">FSCTL_ADD_OVERLAY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn632442">FSCTL_REMOVE_OVERLAY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt426735">FSCTL_SUSPEND_OVERLAY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn632445">FSCTL_UPDATE_OVERLAY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20WIM_PROVIDER_ADD_OVERLAY_INPUT structure%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
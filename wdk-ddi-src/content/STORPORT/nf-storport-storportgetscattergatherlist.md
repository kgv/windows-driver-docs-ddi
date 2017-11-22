---
UID: NF.storport.StorPortGetScatterGatherList
title: StorPortGetScatterGatherList
author: windows-driver-content
description: The StorPortGetScatterGatherList routine retrieves the associated scatter/gather list for the specified SCSI request block (SRB).
old-location: storage\storportgetscattergatherlist.htm
ms.assetid: ddb7052d-b9f3-40f6-b00a-6bf52f010cdc
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortGetScatterGatherList
req.alt-loc: Storport.lib,Storport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Storport.lib
req.dll: 
req.irql: 
ms.keywords: StorPortGetScatterGatherList
req.iface: 
req.product: Windows 10 or later.
---

# StorPortGetScatterGatherList function



## -description
<p>The <b>StorPortGetScatterGatherList</b> routine retrieves the associated scatter/gather list for the specified SCSI request block (SRB). </p>


## -syntax

````
STORPORT_API PSTOR_SCATTER_GATHER_LIST StorPortGetScatterGatherList(
  _In_ PVOID               HwDeviceExtension,
  _In_ PSCSI_REQUEST_BLOCK Srb
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension. This is a per HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the mapped access ranges for the HBA. This area is available to the miniport immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff567108">StorPortInitialize</a>. The port driver frees this memory when it removes the device. </p>
</dd>

### -param <i>Srb</i> [in]

<dd>
<p>Pointer to the SRB for which the scatter gather list is to be constructed. </p>
</dd>
</dl>

## -returns
<p><b>StorPortGetScatterGatherList</b> returns a pointer to the scatter/gather list. </p>

## -remarks
<p>This routine is provided with the Storport driver library. There is no parallel routine provided in the SCSI port library. </p>

<p>The pointer to the scatter/gather list that is returned is valid only until the SRB is completed. </p>

<p>The miniport driver does not have to free the memory for the scatter/gather list that <b>StorPortGetScatterGatherList</b> returns. </p>

<p>The miniport driver must not modify the scatter/gather list.</p>

<p>Starting in Windows 8, the <i>Srb</i> parameter may point to either <a href="https://msdn.microsoft.com/library/windows/hardware/ff565393">SCSI_REQUEST_BLOCK</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/hh451474">STORAGE_REQUEST_BLOCK</a>. If the function identifier in the <b>Function</b> field of <i>Srb</i> is <b>SRB_FUNCTION_STORAGE_REQUEST_BLOCK</b>, the SRB is a <b>STORAGE_REQUEST_BLOCK</b> request structure.</p>

<p>This routine is provided with the Storport driver library. There is no parallel routine provided in the SCSI port library. </p>

<p>The pointer to the scatter/gather list that is returned is valid only until the SRB is completed. </p>

<p>The miniport driver does not have to free the memory for the scatter/gather list that <b>StorPortGetScatterGatherList</b> returns. </p>

<p>The miniport driver must not modify the scatter/gather list.</p>

<p>Starting in Windows 8, the <i>Srb</i> parameter may point to either <a href="https://msdn.microsoft.com/library/windows/hardware/ff565393">SCSI_REQUEST_BLOCK</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/hh451474">STORAGE_REQUEST_BLOCK</a>. If the function identifier in the <b>Function</b> field of <i>Srb</i> is <b>SRB_FUNCTION_STORAGE_REQUEST_BLOCK</b>, the SRB is a <b>STORAGE_REQUEST_BLOCK</b> request structure.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Storport.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565393">SCSI_REQUEST_BLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451474">STORAGE_REQUEST_BLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567588">STOR_SCATTER_GATHER_ELEMENT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567590">STOR_SCATTER_GATHER_LIST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortGetScatterGatherList routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
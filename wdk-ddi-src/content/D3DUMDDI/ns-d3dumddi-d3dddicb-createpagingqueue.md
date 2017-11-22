---
UID: NS.d3dumddi.D3DDDICB_CREATEPAGINGQUEUE
title: D3DDDICB_CREATEPAGINGQUEUE
author: windows-driver-content
description: D3DDDICB_CREATEPAGINGQUEUE is used with pfnCreatePagingQueueCb to create a device paging queue that can be used to synchronize with video memory management operations for the device, such as making the device resource resident.
old-location: display\d3dddicb_createpagingqueue.htm
ms.assetid: 9E36B02F-2292-416C-AA09-1968EECE5A3D
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDICB_CREATEPAGINGQUEUE
req.alt-loc: d3dumddi.h
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
ms.keywords: D3DDDICB_CREATEPAGINGQUEUE, D3DDDICB_CREATEPAGINGQUEUE
req.iface: 
---

# D3DDDICB_CREATEPAGINGQUEUE structure



## -description
<p><b>D3DDDICB_CREATEPAGINGQUEUE</b> is used with <a href="https://msdn.microsoft.com/99E4CFCF-7A0A-43A9-9E23-B7A9F9375690">pfnCreatePagingQueueCb</a> to create a device paging queue that can be used to synchronize with video memory management operations for the device, such as making the device resource resident.</p>


## -syntax

````
typedef struct D3DDDICB_CREATEPAGINGQUEUE {
  D3DDDI_PAGINGQUEUE_PRIORITY Priority;
  D3DKMT_HANDLE               hPagingQueue;
  D3DKMT_HANDLE               hSyncObject;
  VOID                        *FenceValueCPUVirtualAddress;
  UINT                        PhysicalAdapterIndex;
} D3DDDICB_CREATEPAGINGQUEUE;
````


## -struct-fields
<dl>

### -field <b>Priority</b>

<dd>
<p>[in] Scheduling priority relative to other paging queues on this device. Paging queues with higher priority values will be processed ahead of paging queues with lower priority values.</p>
</dd>

### -field <b>hPagingQueue</b>

<dd>
<p>[out] A paging queue handle that will be used to synchronize paging operations.</p>
</dd>

### -field <b>hSyncObject</b>

<dd>
<p>[out] Handle to the monitored fence object used to synchronize paging operations for this paging queue. Destroying the paging queue (either implicitly or explicitly) will automatically destroy this sync object.</p>
</dd>

### -field <b>FenceValueCPUVirtualAddress</b>

<dd>
<p>[out] A read-only mapping of the paging fence object value for the CPU. This is a user mode address readable from the process that created the monitored fence object.</p>
</dd>

### -field <b>PhysicalAdapterIndex</b>

<dd>
<p>[in] Physical adapter index (engine ordinal) for the queue.</p>
</dd>
</dl>

## -remarks
<p>A device can have multiple paging queues created for it. Paging queues can be destroyed either explicitly by calling <a href="https://msdn.microsoft.com/2C039656-5384-4864-8F29-A336B0ED06C0">pfnDestroyPagingQueueCb</a>, or by implicitly destroying the device they belong to. After the latter, paging queue handles will become invalid.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/99E4CFCF-7A0A-43A9-9E23-B7A9F9375690">pfnCreatePagingQueueCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2C039656-5384-4864-8F29-A336B0ED06C0">pfnDestroyPagingQueueCb</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDICB_CREATEPAGINGQUEUE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
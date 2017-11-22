---
UID: NS.1394._IRB_REQ_ASYNC_WRITE
title: IRB_REQ_ASYNC_WRITE
author: windows-driver-content
description: This structure contains the fields necessary for the 1394 stack to carry out an asynchronous write request.
old-location: ieee\irb_req_async_write.htm
ms.assetid: 007E0DDE-0BD1-499D-A6C6-446644BBCE00
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: IEEE
req.header: 1394.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IRB_REQ_ASYNC_WRITE
req.alt-loc: 1394.h
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
ms.keywords: IRB_REQ_ASYNC_WRITE, IRB_REQ_ASYNC_WRITE
---

# IRB_REQ_ASYNC_WRITE structure



## -description
<p>This structure contains the fields necessary for the 1394 stack to carry out an asynchronous write request.</p>


## -syntax

````
typedef struct _IRB_REQ_ASYNC_WRITE {
  IO_ADDRESS DestinationAddress;
  ULONG      nNumberOfBytesToWrite;
  ULONG      nBlockSize;
  ULONG      fulFlags;
  PMDL       Mdl;
  ULONG      ulGeneration;
  UCHAR      chPriority;
  UCHAR      nSpeed;
  UCHAR      tCode;
  UCHAR      Reserved;
  ULONG      ElapsedTime;
} IRB_REQ_ASYNC_WRITE;
````


## -struct-fields
<dl>

### -field <b>DestinationAddress</b>

<dd>
<p>Specifies the 1394 64-bit destination address for this write operation. The driver only must fill in the <b>IA_Destination_Offset</b> member of <b>u.AsyncWrite.DestinationAddress</b>; the bus driver fills in the <b>IA_Destination_ID</b> member. See <a href="https://msdn.microsoft.com/library/windows/hardware/ff537346">IO_ADDRESS</a> for the structure description.</p>
</dd>

### -field <b>nNumberOfBytesToWrite</b>

<dd>
<p>Specifies the number of bytes to write to the 1394 node.</p>
</dd>

### -field <b>nBlockSize</b>

<dd>
<p>Specifies the size of each individual block within the data stream that is written as a whole to the node. If this parameter is zero, then the maximum packet size for the speed selected is used in breaking up these write requests, unless raw-mode addressing is used.</p>
<p>

If raw-mode addressing is used, the client driver should set the <b>nBlockSize</b> member to the maximum asynchronous payload size that is supported by the device at the connected speed. </p>
<p>For more information on raw-mode addressing, see <a href="https://msdn.microsoft.com/93ad0cdf-5ac2-4916-b90e-1e64ca4494b6">Sending Asynchronous I/O Request Packets on the IEEE 1394 Bus.</a>
</p>
<div class="alert"><b>Note</b>  In Windows 7 and later versions of Windows, you can specify new values higher speed and  greater sized payloads. For more information, see <a href="buses.device_driver_interface__ddi__changes_in_windows_7#speed#speed">New Flags for Speed and Payload Size</a> and <a href="buses.device_driver_interface__ddi__changes_in_windows_7#ioctl#ioctl">IEEE 1394 IOCTL Changes</a> in Device Driver Interface (DDI) Changes in Windows 7.</div>
<div> </div>
</dd>

### -field <b>fulFlags</b>

<dd>
<p>Specifies any nondefault settings for this operation. The following flags are provided.</p>
<table>
<tr>
<th>Flag</th>
<th>Description</th>
</tr>
<tr>
<td>
<p> ASYNC_FLAGS_NONINCREMENTING</p>
</td>
<td>
<p>Do not increment 1394 address during asynchronous operation. This flag is set only in large asynchronous requests (that is, those greater than asynchronous packet size).</p>
</td>
</tr>
<tr>
<td>
<p>ASYNC_FLAGS_NO_STATUS</p>
</td>
<td>
<p>Always return success from the write operation, whether the write succeeds or fails.</p>
</td>
</tr>
<tr>
<td>
<p>ASYNC_FLAGS_BROADCAST</p>
</td>
<td>
<p>Broadcast to all nodes on the bus.</p>
</td>
</tr>
</table>
<p> </p>
<p>Use the bitwise operator OR to combine the settings.</p>
</dd>

### -field <b>Mdl</b>

<dd>
<p>Points to an MDL that describes the device driver's buffer, which receives data from the 1394 node.</p>
</dd>

### -field <b>ulGeneration</b>

<dd>
<p>Specifies the bus reset generation as known by the device driver that submitted this asynchronous request. If the generation count specified does not match the actual generation of the bus, this request is returned with a status of STATUS_INVALID_GENERATION.  </p>
</dd>

### -field <b>chPriority</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>nSpeed</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>tCode</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>ElapsedTime</b>

<dd>
<p>Elapsed time in nanoseconds. Only valid for flag <b>ASYNC_FLAGS_PING</b>.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>1394.h</dt>
</dl>
</td>
</tr>
</table>
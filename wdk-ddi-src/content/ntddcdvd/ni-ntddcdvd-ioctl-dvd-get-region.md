---
UID: NI.ntddcdvd.IOCTL_DVD_GET_REGION
title: IOCTL_DVD_GET_REGION
author: windows-driver-content
description: 
ms.assetid: 65220064-6067-4659-853a-309a12ca9761
ms.author: windowsdriverdev
ms.date: 
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ntddcdvd.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.irql: 
req.ddi-compliance:
req.alt-api:
req.alt-loc:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library:
---

# IOCTL_DVD_GET_REGION IOCTL

## Major Code:  [[XREF-LINK:IRP_MJ_DEVICE_CONTROL]

## -description



## -ioctlparameters

### -input-buffer

<text></text>

### -input-buffer-length 

<text></text>

### -output-buffer

<text></text>

### -output-buffer-length 

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length 

<text></text>

### -status-block

Irp->IoStatus.Status is set to STATUS_SUCCESS if the request is successful.
Otherwise, Status to the appropriate error condition as a NTSTATUS code. 
For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

## -see-also
---
UID: NI.nfcradiodev.IOCTL_NFCSERM_SET_RADIO_STATE
title: IOCTL_NFCSERM_SET_RADIO_STATE
author: windows-driver-content
description: 
ms.assetid: 54ec8738-2da9-49b5-a3b4-67b1e299b2f9
ms.author: windowsdriverdev
ms.date: 
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: nfcradiodev.h
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

# IOCTL_NFCSERM_SET_RADIO_STATE IOCTL

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
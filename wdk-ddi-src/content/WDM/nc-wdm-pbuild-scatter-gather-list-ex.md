---
UID: NC.wdm.PBUILD_SCATTER_GATHER_LIST_EX
title: PBUILD_SCATTER_GATHER_LIST_EX
author: windows-driver-content
description: 
ms.assetid: 67acd6c3-ed90-41fb-8348-7d74436e47b3
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdm.h
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

# PBUILD_SCATTER_GATHER_LIST_EX callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PBUILD_SCATTER_GATHER_LIST_EX PbuildScatterGatherListEx; 

// Definition

NTSTATUS PbuildScatterGatherListEx 
(
	PDMA_ADAPTER DmaAdapter
	PDEVICE_OBJECT DeviceObject
	PVOID DmaTransferContext
	PMDL Mdl
	ULONGLONG Offset
	ULONG Length
	ULONG Flags
	PDRIVER_LIST_CONTROL ExecutionRoutine
	PVOID Context
	BOOLEAN WriteToDevice
	PVOID ScatterGatherBuffer
	ULONG ScatterGatherLength
	PDMA_COMPLETION_ROUTINE DmaCompletionRoutine
	PVOID CompletionContext
	PVOID ScatterGatherList
)
{...}

PBUILD_SCATTER_GATHER_LIST_EX 


```

## -parameters

### -param DmaAdapter: 
### -param DeviceObject: 
### -param DmaTransferContext: 
### -param Mdl: 
### -param Offset: 
### -param Length: 
### -param Flags: 
### -param ExecutionRoutine: 
### -param Context: 
### -param WriteToDevice: 
### -param ScatterGatherBuffer: 
### -param ScatterGatherLength: 
### -param DmaCompletionRoutine: 
### -param CompletionContext: 
### -param ScatterGatherList: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
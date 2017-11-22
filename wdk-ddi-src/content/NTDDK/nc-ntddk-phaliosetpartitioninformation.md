---
UID: NC.ntddk.pHalIoSetPartitionInformation
title: pHalIoSetPartitionInformation
author: windows-driver-content
description: 
ms.assetid: 888575c3-8c77-4468-9587-d87e4ce1d05b
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ntddk.h
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

# pHalIoSetPartitionInformation callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

pHalIoSetPartitionInformation Phaliosetpartitioninformation; 

// Definition

NTSTATUS Phaliosetpartitioninformation 
(
	PDEVICE_OBJECT DeviceObject
	ULONG SectorSize
	ULONG PartitionNumber
	ULONG PartitionType
)
{...}

pHalIoSetPartitionInformation 


```

## -parameters

### -param DeviceObject: 
### -param SectorSize: 
### -param PartitionNumber: 
### -param PartitionType: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
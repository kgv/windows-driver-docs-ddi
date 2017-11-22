---
UID: NC.wdm.ALLOCATE_FUNCTION_EX
title: ALLOCATE_FUNCTION_EX
author: windows-driver-content
description: 
ms.assetid: a9759071-af1c-43da-b4cc-5928f890d2ed
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

# ALLOCATE_FUNCTION_EX callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

ALLOCATE_FUNCTION_EX AllocateFunctionEx; 

// Definition

PVOID AllocateFunctionEx 
(
	POOL_TYPE PoolType
	SIZE_T NumberOfBytes
	ULONG Tag
	PLOOKASIDE_LIST_EX Lookaside
)
{...}

ALLOCATE_FUNCTION_EX PALLOCATE_FUNCTION_EX


```

## -parameters

### -param PoolType: 
### -param NumberOfBytes: 
### -param Tag: 
### -param Lookaside: 



## -returns

Returns PVOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
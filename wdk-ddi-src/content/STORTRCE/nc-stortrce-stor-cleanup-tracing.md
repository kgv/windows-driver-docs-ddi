---
UID: NC.stortrce.STOR_CLEANUP_TRACING
title: STOR_CLEANUP_TRACING
author: windows-driver-content
description: 
ms.assetid: 0374531e-3b33-4750-ba00-a939861dea0d
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: stortrce.h
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

# STOR_CLEANUP_TRACING callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

STOR_CLEANUP_TRACING StorCleanupTracing; 

// Definition

VOID StorCleanupTracing 
(
	PVOID Arg1
)
{...}

STOR_CLEANUP_TRACING 


```

## -parameters

### -param Arg1: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
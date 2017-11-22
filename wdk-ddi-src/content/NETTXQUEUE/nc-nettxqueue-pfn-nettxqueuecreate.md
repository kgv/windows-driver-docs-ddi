---
UID: NC.nettxqueue.PFN_NETTXQUEUECREATE
title: PFN_NETTXQUEUECREATE
author: windows-driver-content
description: 
ms.assetid: 02a8831b-1e35-475e-9e6a-c101ac4ef542
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: nettxqueue.h
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

# PFN_NETTXQUEUECREATE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_NETTXQUEUECREATE PfnNettxqueuecreate; 

// Definition

WDFAPI PfnNettxqueuecreate 
(
	PNET_DRIVER_GLOBALS DriverGlobals
	PNETTXQUEUE_INIT NetTxQueueInit
	PWDF_OBJECT_ATTRIBUTES TxQueueAttributes
	PNET_TXQUEUE_CONFIG Configuration
	NETTXQUEUE *TxQueue
)
{...}

PFN_NETTXQUEUECREATE 


```

## -parameters

### -param DriverGlobals: 
### -param NetTxQueueInit: 
### -param TxQueueAttributes: 
### -param Configuration: 
### -param *TxQueue: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
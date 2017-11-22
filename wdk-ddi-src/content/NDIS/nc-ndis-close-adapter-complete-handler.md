---
UID: NC.ndis.CLOSE_ADAPTER_COMPLETE_HANDLER
title: CLOSE_ADAPTER_COMPLETE_HANDLER
author: windows-driver-content
description: 
ms.assetid: 67971280-130e-49f0-98fb-7293278d8c00
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ndis.h
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

# CLOSE_ADAPTER_COMPLETE_HANDLER callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

CLOSE_ADAPTER_COMPLETE_HANDLER CloseAdapterCompleteHandler; 

// Definition

VOID CloseAdapterCompleteHandler 
(
	NDIS_HANDLE ProtocolBindingContext
	NDIS_STATUS Status
)
{...}

CLOSE_ADAPTER_COMPLETE_HANDLER 


```

## -parameters

### -param ProtocolBindingContext: 
### -param Status: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
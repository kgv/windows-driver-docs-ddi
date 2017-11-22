---
UID: NC.wdfresource.PFN_WDFCMRESOURCELISTAPPENDDESCRIPTOR
title: PFN_WDFCMRESOURCELISTAPPENDDESCRIPTOR
author: windows-driver-content
description: 
ms.assetid: feba2412-0ce9-4487-aa3d-8ba7095ecf9b
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfresource.h
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

# PFN_WDFCMRESOURCELISTAPPENDDESCRIPTOR callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFCMRESOURCELISTAPPENDDESCRIPTOR PfnWdfcmresourcelistappenddescriptor; 

// Definition

WDFAPI PfnWdfcmresourcelistappenddescriptor 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFCMRESLIST List
	PCM_PARTIAL_RESOURCE_DESCRIPTOR Descriptor
)
{...}

PFN_WDFCMRESOURCELISTAPPENDDESCRIPTOR 


```

## -parameters

### -param DriverGlobals: 
### -param List: 
### -param Descriptor: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
---
UID: NC.wdfchildlist.PFN_WDFCHILDLISTBEGINITERATION
title: PFN_WDFCHILDLISTBEGINITERATION
author: windows-driver-content
description: 
ms.assetid: ead8d425-fd53-4bcf-80b4-883d021ea5ea
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfchildlist.h
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

# PFN_WDFCHILDLISTBEGINITERATION callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFCHILDLISTBEGINITERATION PfnWdfchildlistbeginiteration; 

// Definition

WDFAPI PfnWdfchildlistbeginiteration 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFCHILDLIST ChildList
	PWDF_CHILD_LIST_ITERATOR Iterator
)
{...}

PFN_WDFCHILDLISTBEGINITERATION 


```

## -parameters

### -param DriverGlobals: 
### -param ChildList: 
### -param Iterator: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
---
UID: NC.wdfrequest.PFN_WDFREQUESTCHANGETARGET
title: PFN_WDFREQUESTCHANGETARGET
author: windows-driver-content
description: 
ms.assetid: 6fc1b3ab-9c09-42bd-9294-ca22edd9a2e8
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfrequest.h
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

# PFN_WDFREQUESTCHANGETARGET callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFREQUESTCHANGETARGET PfnWdfrequestchangetarget; 

// Definition

WDFAPI PfnWdfrequestchangetarget 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFREQUEST Request
	WDFIOTARGET IoTarget
)
{...}

PFN_WDFREQUESTCHANGETARGET 


```

## -parameters

### -param DriverGlobals: 
### -param Request: 
### -param IoTarget: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
---
UID: NC.wdfrequest.PFN_WDFREQUESTSETINFORMATION
title: PFN_WDFREQUESTSETINFORMATION
author: windows-driver-content
description: 
ms.assetid: 3bfacf9d-28ac-470f-8b2e-e75a6bc9457a
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

# PFN_WDFREQUESTSETINFORMATION callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFREQUESTSETINFORMATION PfnWdfrequestsetinformation; 

// Definition

WDFAPI PfnWdfrequestsetinformation 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFREQUEST Request
	ULONG_PTR Information
)
{...}

PFN_WDFREQUESTSETINFORMATION 


```

## -parameters

### -param DriverGlobals: 
### -param Request: 
### -param Information: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
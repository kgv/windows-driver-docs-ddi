---
UID: NC.wdfdevice.PFN_WDFDEVICECONFIGUREREQUESTDISPATCHING
title: PFN_WDFDEVICECONFIGUREREQUESTDISPATCHING
author: windows-driver-content
description: 
ms.assetid: d5c1591a-2807-43dd-bff7-88e21a610866
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfdevice.h
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

# PFN_WDFDEVICECONFIGUREREQUESTDISPATCHING callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFDEVICECONFIGUREREQUESTDISPATCHING PfnWdfdeviceconfigurerequestdispatching; 

// Definition

WDFAPI PfnWdfdeviceconfigurerequestdispatching 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFDEVICE Device
	WDFQUEUE Queue
	_Strict_type_match_ WDF_REQUEST_TYPE
)
{...}

PFN_WDFDEVICECONFIGUREREQUESTDISPATCHING 


```

## -parameters

### -param DriverGlobals: 
### -param Device: 
### -param Queue: 
### -param WDF_REQUEST_TYPE: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
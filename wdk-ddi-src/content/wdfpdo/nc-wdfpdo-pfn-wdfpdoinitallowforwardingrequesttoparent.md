---
UID: NC.wdfpdo.PFN_WDFPDOINITALLOWFORWARDINGREQUESTTOPARENT
title: PFN_WDFPDOINITALLOWFORWARDINGREQUESTTOPARENT
author: windows-driver-content
description: 
ms.assetid: 0086f6b4-d32e-4169-95e2-e0956f4a066a
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfpdo.h
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

# PFN_WDFPDOINITALLOWFORWARDINGREQUESTTOPARENT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFPDOINITALLOWFORWARDINGREQUESTTOPARENT PfnWdfpdoinitallowforwardingrequesttoparent; 

// Definition

WDFAPI PfnWdfpdoinitallowforwardingrequesttoparent 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	PWDFDEVICE_INIT DeviceInit
)
{...}

PFN_WDFPDOINITALLOWFORWARDINGREQUESTTOPARENT 


```

## -parameters

### -param DriverGlobals: 
### -param DeviceInit: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
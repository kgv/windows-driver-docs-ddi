---
UID: NC.wdfpdo.PFN_WDFPDOGETPARENT
title: PFN_WDFPDOGETPARENT
author: windows-driver-content
description: 
ms.assetid: 3e11df49-92ee-4235-abd4-4d2156ae8b2d
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

# PFN_WDFPDOGETPARENT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFPDOGETPARENT PfnWdfpdogetparent; 

// Definition

WDFAPI PfnWdfpdogetparent 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFDEVICE Device
)
{...}

PFN_WDFPDOGETPARENT 


```

## -parameters

### -param DriverGlobals: 
### -param Device: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
---
UID: NC.d3d10umddi.PFND3DWDDM2_2DDI_RELOCATEDEVICEFUNCS
title: PFND3DWDDM2_2DDI_RELOCATEDEVICEFUNCS
author: windows-driver-content
description: 
ms.assetid: eb4a5bb8-f90f-4d05-9a30-c89ad415653c
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3d10umddi.h
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

# PFND3DWDDM2_2DDI_RELOCATEDEVICEFUNCS callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3DWDDM2_2DDI_RELOCATEDEVICEFUNCS Pfnd3dwddm22DdiRelocatedevicefuncs; 

// Definition

VOID Pfnd3dwddm22DdiRelocatedevicefuncs 
(
	 D3D10DDI_HDEVICE
	D3DWDDM2_2DDI_DEVICEFUNCS *
)
{...}

PFND3DWDDM2_2DDI_RELOCATEDEVICEFUNCS 


```

## -parameters

### -param D3D10DDI_HDEVICE: 
### -param *: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
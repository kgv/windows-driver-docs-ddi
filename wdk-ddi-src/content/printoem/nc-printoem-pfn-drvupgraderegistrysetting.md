---
UID: NC.printoem.PFN_DrvUpgradeRegistrySetting
title: PFN_DrvUpgradeRegistrySetting
author: windows-driver-content
description: 
ms.assetid: 949981a8-781b-42b5-b68b-a5575414694d
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: printoem.h
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

# PFN_DrvUpgradeRegistrySetting callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_DrvUpgradeRegistrySetting PfnDrvupgraderegistrysetting; 

// Definition

BOOL PfnDrvupgraderegistrysetting 
(
	HANDLE hPrinter
	PCSTR pFeature
	PCSTR pOption
)
{...}

PFN_DrvUpgradeRegistrySetting 


```

## -parameters

### -param hPrinter: 
### -param pFeature: 
### -param pOption: 



## -returns

Returns BOOL that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
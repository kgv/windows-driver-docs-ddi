---
UID: NC.wdfdmatransaction.PFN_WDFDMATRANSACTIONWDMGETTRANSFERCONTEXT
title: PFN_WDFDMATRANSACTIONWDMGETTRANSFERCONTEXT
author: windows-driver-content
description: 
ms.assetid: 1501284b-b473-41ec-9fb5-53997a1a3390
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfdmatransaction.h
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

# PFN_WDFDMATRANSACTIONWDMGETTRANSFERCONTEXT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFDMATRANSACTIONWDMGETTRANSFERCONTEXT PfnWdfdmatransactionwdmgettransfercontext; 

// Definition

WDFAPI PfnWdfdmatransactionwdmgettransfercontext 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFDMATRANSACTION DmaTransaction
)
{...}

PFN_WDFDMATRANSACTIONWDMGETTRANSFERCONTEXT 


```

## -parameters

### -param DriverGlobals: 
### -param DmaTransaction: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
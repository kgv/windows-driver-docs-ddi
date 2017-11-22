---
UID: NC.trustedruntimeclx.EVT_TR_CONNECT_SECURE_SERVICE
title: EVT_TR_CONNECT_SECURE_SERVICE
author: windows-driver-content
description: 
ms.assetid: cb3b1b90-9795-41e0-8a3a-c290f7e26865
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: trustedruntimeclx.h
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

# EVT_TR_CONNECT_SECURE_SERVICE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

EVT_TR_CONNECT_SECURE_SERVICE EvtTrConnectSecureService; 

// Definition

NTSTATUS EvtTrConnectSecureService 
(
	WDFDEVICE ServiceDevice
)
{...}

EVT_TR_CONNECT_SECURE_SERVICE PFN_TR_CONNECT_SECURE_SERVICE


```

## -parameters

### -param ServiceDevice: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
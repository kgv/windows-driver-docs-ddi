---
UID: NC.wsk.PFN_WSK_BIND
title: PFN_WSK_BIND
author: windows-driver-content
description: 
ms.assetid: aca1aacc-8ee8-4f33-9de1-6ca464ca8474
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wsk.h
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

# PFN_WSK_BIND callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WSK_BIND PfnWskBind; 

// Definition

NTSTATUS PfnWskBind 
(
	PWSK_SOCKET Socket
	PSOCKADDR LocalAddress
	ULONG Flags
	PIRP Irp
)
{...}

PFN_WSK_BIND 


```

## -parameters

### -param Socket: 
### -param LocalAddress: 
### -param Flags: 
### -param Irp: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
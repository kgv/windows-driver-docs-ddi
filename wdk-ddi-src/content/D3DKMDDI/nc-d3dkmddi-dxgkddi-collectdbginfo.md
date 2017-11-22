---
UID: NC.d3dkmddi.DXGKDDI_COLLECTDBGINFO
title: DXGKDDI_COLLECTDBGINFO
author: windows-driver-content
description: 
ms.assetid: cd0d2d4a-7683-4abe-a6ef-02e24c7d9ff4
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3dkmddi.h
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

# DXGKDDI_COLLECTDBGINFO callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

DXGKDDI_COLLECTDBGINFO DxgkddiCollectdbginfo; 

// Definition

NTSTATUS DxgkddiCollectdbginfo 
(
	IN_CONST_HANDLE hAdapter
	IN_CONST_PDXGKARG_COLLECTDBGINFO pCollectDbgInfo
)
{...}

DXGKDDI_COLLECTDBGINFO PDXGKDDI_COLLECTDBGINFO


```

## -parameters

### -param hAdapter: 
### -param pCollectDbgInfo: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
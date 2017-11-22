---
UID: NC.d3dkmddi.DXGKDDI_BUILDPAGINGBUFFER
title: DXGKDDI_BUILDPAGINGBUFFER
author: windows-driver-content
description: 
ms.assetid: 67c6fbce-065a-4ce0-89bb-242af57016d1
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

# DXGKDDI_BUILDPAGINGBUFFER callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

DXGKDDI_BUILDPAGINGBUFFER DxgkddiBuildpagingbuffer; 

// Definition

NTSTATUS DxgkddiBuildpagingbuffer 
(
	IN_CONST_HANDLE hAdapter
	IN_PDXGKARG_BUILDPAGINGBUFFER pBuildPagingBuffer
)
{...}

DXGKDDI_BUILDPAGINGBUFFER PDXGKDDI_BUILDPAGINGBUFFER


```

## -parameters

### -param hAdapter: 
### -param pBuildPagingBuffer: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
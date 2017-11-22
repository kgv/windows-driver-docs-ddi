---
UID: NC.d3dkmddi.DXGKDDI_SUBMITCOMMANDVIRTUAL
title: DXGKDDI_SUBMITCOMMANDVIRTUAL
author: windows-driver-content
description: 
ms.assetid: 7cbf890a-aef1-4cc6-acd6-7790032e26a8
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

# DXGKDDI_SUBMITCOMMANDVIRTUAL callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

DXGKDDI_SUBMITCOMMANDVIRTUAL DxgkddiSubmitcommandvirtual; 

// Definition

NTSTATUS DxgkddiSubmitcommandvirtual 
(
	IN_CONST_HANDLE hAdapter
	IN_CONST_PDXGKARG_SUBMITCOMMANDVIRTUAL pSubmitCommand
)
{...}

DXGKDDI_SUBMITCOMMANDVIRTUAL PDXGKDDI_SUBMITCOMMANDVIRTUAL


```

## -parameters

### -param hAdapter: 
### -param pSubmitCommand: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
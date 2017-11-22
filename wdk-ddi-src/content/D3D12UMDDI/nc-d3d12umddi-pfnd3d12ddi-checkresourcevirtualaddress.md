---
UID: NC.d3d12umddi.PFND3D12DDI_CHECKRESOURCEVIRTUALADDRESS
title: PFND3D12DDI_CHECKRESOURCEVIRTUALADDRESS
author: windows-driver-content
description: 
ms.assetid: b6bb2805-e4d5-4975-a039-8d194c1d4b60
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3d12umddi.h
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

# PFND3D12DDI_CHECKRESOURCEVIRTUALADDRESS callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3D12DDI_CHECKRESOURCEVIRTUALADDRESS Pfnd3d12ddiCheckresourcevirtualaddress; 

// Definition

D3D12DDI_GPU_VIRTUAL_ADDRESS Pfnd3d12ddiCheckresourcevirtualaddress 
(
	 D3D12DDI_HDEVICE
	 D3D12DDI_HRESOURCE
)
{...}

PFND3D12DDI_CHECKRESOURCEVIRTUALADDRESS 


```

## -parameters

### -param D3D12DDI_HDEVICE: 
### -param D3D12DDI_HRESOURCE: 



## -returns

Returns D3D12DDI_GPU_VIRTUAL_ADDRESS that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also
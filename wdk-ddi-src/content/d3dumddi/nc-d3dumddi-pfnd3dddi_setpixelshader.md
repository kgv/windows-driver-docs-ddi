---
UID: NC:d3dumddi.PFND3DDDI_SETPIXELSHADER
title: PFND3DDDI_SETPIXELSHADER
author: windows-driver-content
description: The SetPixelShader function sets a pixel shader to be used in all drawing operations.
old-location: display\setpixelshader.htm
old-project: display
ms.assetid: b7ffd96d-086e-445a-89cf-6f34a5b8a5d4
ms.author: windowsdriverdev
ms.date: 3/29/2018
ms.keywords: PFND3DDDI_SETPIXELSHADER, SetPixelShader, SetPixelShader callback function [Display Devices], UserModeDisplayDriver_Functions_dd7fa75c-0753-4786-b04a-2fdd0d0e7071.xml, d3dumddi/SetPixelShader, display.setpixelshader
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	d3dumddi.h
api_name:
-	SetPixelShader
product:
- Windows
targetos: Windows
req.typenames: DXGK_PTE
---

# PFND3DDDI_SETPIXELSHADER callback


## -description


The <i>SetPixelShader</i> function sets a pixel shader to be used in all drawing operations. 


## -parameters




### -param hDevice [in]

 A handle to the display device (graphics context).


### -param Arg1








#### - hShaderHandle [in]

 A handle to the pixel shader code object.


## -returns



<i>SetPixelShader</i> returns S_OK or an appropriate error result if the pixel shader is not successfully set.




## -remarks



All subsequent drawing operations use the given shader until another is selected.

For user-mode display drivers that support pixel shaders before version 2.0, the Microsoft Direct3D runtime passes 0 in the <i>hShaderHandle</i> parameter to indicate a fixed-function pipeline. For user-mode display drivers that support pixel shader version 2.0 or later, the runtime converts Direct3D fixed-function pixel state to pixel shader version 2.0. For more information about fixed-function state, see <a href="https://msdn.microsoft.com/bc93d65e-ac16-470d-8c52-db8b1cc74456">Converting the Direct3D Fixed-Function State</a>.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff544519">D3DDDI_DEVICEFUNCS</a>
 

 


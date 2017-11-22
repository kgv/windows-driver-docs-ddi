---
UID: NC.d3d10umddi.PFND3D10DDI_QUERYEND
title: PFND3D10DDI_QUERYEND
author: windows-driver-content
description: The QueryEnd function marks the end of a sequence of graphics commands for a query and transitions the query to the &#0034;issued&#0034; state.
old-location: display\queryend.htm
ms.assetid: 5a231d7e-7e47-40ad-99d1-82661dec41d0
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: QueryEnd
req.alt-loc: d3d10umddi.h
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
ms.keywords: SETRESULT_INFO, SETRESULT_INFO, *PSETRESULT_INFO
req.iface: 
---

# PFND3D10DDI_QUERYEND callback



## -description
<p>The <i>QueryEnd</i> function marks the end of a sequence of graphics commands for a query and transitions the query to the "issued" state. </p>


## -prototype

````
PFND3D10DDI_QUERYEND QueryEnd;

VOID APIENTRY QueryEnd(
  _In_ D3D10DDI_HDEVICE hDevice,
  _In_ D3D10DDI_HQUERY  hQuery
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to the display device (graphics context).</p>
</dd>

### -param <i>hQuery</i> [in]

<dd>
<p> A handle to the query object to end.</p>
</dd>
</dl>

## -returns
<p>None</p>

<p>The driver can use the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> callback function to set an error code. For more information about setting error codes, see the following Remarks section.</p>

## -remarks
<p>If the driver supports the <a href="https://msdn.microsoft.com/2f0a7462-83a6-47df-b5f6-b3706b875349">QueryBegin</a> function for a query operation, and if the Microsoft Direct3D runtime calls <i>QueryEnd</i> without call <i>QueryBegin</i>, the call is equivalent to first calling <i>QueryBegin</i> and then calling <i>QueryEnd</i> immediately afterward. In addition, the runtime cannot call <i>QueryEnd</i> on a predicate that is currently bound to the pipeline through a call to the <a href="https://msdn.microsoft.com/df671478-859f-4ccd-9ab4-1986f9af10cf">SetPredication</a> function.</p>

<p>The driver should not encounter any error, except for D3DDDIERR_DEVICEREMOVED. Therefore, if the driver passes any error, except for D3DDDIERR_DEVICEREMOVED, in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function, the Direct3D runtime will determine that the error is critical. Even if the device was removed, the driver is not required to return D3DDDIERR_DEVICEREMOVED; however, if device removal interfered with the operation of <i>QueryEnd</i> (which typically should not happen), the driver can return D3DDDIERR_DEVICEREMOVED.</p>

<p>If the driver supports the <a href="https://msdn.microsoft.com/2f0a7462-83a6-47df-b5f6-b3706b875349">QueryBegin</a> function for a query operation, and if the Microsoft Direct3D runtime calls <i>QueryEnd</i> without call <i>QueryBegin</i>, the call is equivalent to first calling <i>QueryBegin</i> and then calling <i>QueryEnd</i> immediately afterward. In addition, the runtime cannot call <i>QueryEnd</i> on a predicate that is currently bound to the pipeline through a call to the <a href="https://msdn.microsoft.com/df671478-859f-4ccd-9ab4-1986f9af10cf">SetPredication</a> function.</p>

<p>The driver should not encounter any error, except for D3DDDIERR_DEVICEREMOVED. Therefore, if the driver passes any error, except for D3DDDIERR_DEVICEREMOVED, in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function, the Direct3D runtime will determine that the error is critical. Even if the device was removed, the driver is not required to return D3DDDIERR_DEVICEREMOVED; however, if device removal interfered with the operation of <i>QueryEnd</i> (which typically should not happen), the driver can return D3DDDIERR_DEVICEREMOVED.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541833">D3D10DDI_DEVICEFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2f0a7462-83a6-47df-b5f6-b3706b875349">QueryBegin</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/df671478-859f-4ccd-9ab4-1986f9af10cf">SetPredication</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D10DDI_QUERYEND callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NC.d3dkmddi.DXGKCB_QUERYVIDPNINTERFACE
title: DXGKCB_QUERYVIDPNINTERFACE
author: windows-driver-content
description: The DxgkCbQueryVidPnInterface function returns a pointer to a DXGK_VIDPN_INTERFACE structure. The structure contains pointers to functions that the display miniport driver can call to inspect and alter a VidPN object.
old-location: display\dxgkcbqueryvidpninterface.htm
ms.assetid: 649ce7fc-6852-43f3-b944-b2b64fcba874
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DxgkCbQueryVidPnInterface
req.alt-loc: d3dkmddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: DD_MULTISAMPLEQUALITYLEVELSDATA, DD_MULTISAMPLEQUALITYLEVELSDATA
req.iface: 
---

# DXGKCB_QUERYVIDPNINTERFACE callback



## -description
<p>The <b>DxgkCbQueryVidPnInterface</b> function returns a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> structure. The structure contains pointers to functions that the display miniport driver can call to inspect and alter a VidPN object.</p>


## -prototype

````
DXGKCB_QUERYVIDPNINTERFACE DxgkCbQueryVidPnInterface;

NTSTATUS APIENTRY DxgkCbQueryVidPnInterface(
  _In_  const D3DKMDT_HVIDPN               hVidPn,
  _In_  const DXGK_VIDPN_INTERFACE_VERSION VidPnInterfaceVersion,
  _Out_ const DXGK_VIDPN_INTERFACE         **ppVidPnInterface
)
{ ... }
````


## -parameters
<dl>

### -param <i>hVidPn</i> [in]

<dd>
<p>[in] A handle to a VidPN object. The VidPN manager previously provided the display miniport driver with this handle by calling <a href="https://msdn.microsoft.com/6dda82bd-1a43-4ffe-b398-a9f8cee6d1c1">DxgkDdiEnumVidPnCofuncModality</a>, <a href="https://msdn.microsoft.com/96e96366-6306-4d20-8752-e942f2ed4069">DxgkDdiIsSupportedVidPn</a>, or <a href="https://msdn.microsoft.com/320a77a7-d7d4-47b9-8a40-2b6e12819e4b">DxgkDdiRecommendFunctionalVidPn</a>.</p>
</dd>

### -param <i>VidPnInterfaceVersion</i> [in]

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff562860">DXGK_VIDPN_INTERFACE_VERSION</a> enumerator that specifies the version of the VidPN interface being requested. Callers must set this parameter to <b>DXGK_VIDPN_INTERFACE_VERSION_V1</b>.</p>
</dd>

### -param <i>ppVidPnInterface</i> [out]

<dd>
<p>[out] A pointer to a variable that receives a pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> structure.</p>
</dd>
</dl>

## -returns
<p><b>DxgkCbQueryVidPnInterface </b>returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The function succeeded.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The value passed to <i>ppVidPnInterface</i> is not valid.</p><dl>
<dt><b>STATUS_GRAPHICS_INVALID_VIDPN</b></dt>
</dl><p>The handle passed to <i>hVidPn</i> is not valid.</p><dl>
<dt><b>STATUS_NOT_SUPPORTED</b></dt>
</dl><p>The interface version specified by <i>VidPnInterfaceVersion</i> is not supported.</p>

<p> </p>

<p>The following code example shows how to acquire the VidPN-object-management interface from the Microsoft DirectX graphics kernel subsystem (<i>Dxgkrnl.sys</i>).</p>

## -remarks


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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570556">VidPN Interface</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570560">VidPN Topology Interface</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570558">VidPN Source Mode Set Interface</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570559">VidPN Target Mode Set Interface</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568435">Monitor Source Mode Set Interface</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKCB_QUERYVIDPNINTERFACE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
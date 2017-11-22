---
UID: NF.wiamdef.wiasUpdateScanRect
title: wiasUpdateScanRect
author: windows-driver-content
description: The wiasUpdateScanRect function updates the scanning area sizes of the scanning device.
old-location: image\wiasupdatescanrect.htm
ms.assetid: f8184ae1-878f-46fc-bddc-66c065bc9e75
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: image
req.header: wiamdef.h
req.include-header: Wiamdef.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Microsoft Windows Me and in Windows XP and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: wiasUpdateScanRect
req.alt-loc: Wiaservc.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wiaservc.lib
req.dll: Wiaservc.dll
req.irql: 
ms.keywords: wiasUpdateScanRect
req.iface: 
req.product: Windows 10 or later.
---

# wiasUpdateScanRect function



## -description
<p>The <b>wiasUpdateScanRect</b> function updates the scanning area sizes of the scanning device.</p>


## -syntax

````
HRESULT _stdcall wiasUpdateScanRect(
  _In_ BYTE                 *pWiasContext,
  _In_ WIA_PROPERTY_CONTEXT *pContext,
       LONG                 lWidth,
       LONG                 lHeight
);
````


## -parameters
<dl>

### -param <i>pWiasContext</i> [in]

<dd>
<p>Pointer to a WIA item context.</p>
</dd>

### -param <i>pContext</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552749">WIA_PROPERTY_CONTEXT</a> structure containing the property context, created by a prior call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549167">wiasCreatePropContext</a>.</p>
</dd>

### -param <i>lWidth</i> 

<dd>
<p>Specifies the horizontal width of the scanning area of the scanning device, in units of thousandths of an inch. Normally, this is the horizontal bed size.</p>
</dd>

### -param <i>lHeight</i> 

<dd>
<p>Specifies the vertical height of the scanning area of the scanning device, in units of thousandths of an inch. Normally, this is the vertical bed size.</p>
</dd>
</dl>

## -returns
<p>On success, the function returns S_OK. If the function fails, it returns a standard COM error or one of the WIA_ERROR_XXX errors (described in the Microsoft Windows SDK documentation).</p>

## -remarks
<p>This helper method is called to update the properties making up the scan rectangle. The appropriate changes are made to the properties that are dependent on those that make up the scan rectangle. For example, a change in horizontal resolution affects the horizontal extent. This function assumes that the valid values for the vertical and horizontal extents, and vertical and horizontal positions have not yet been updated. </p>

<p>This helper method is called to update the properties making up the scan rectangle. The appropriate changes are made to the properties that are dependent on those that make up the scan rectangle. For example, a change in horizontal resolution affects the horizontal extent. This function assumes that the valid values for the vertical and horizontal extents, and vertical and horizontal positions have not yet been updated. </p>

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
<p>Available in Microsoft Windows Me and in Windows XP and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wiamdef.h (include Wiamdef.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wiaservc.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Wiaservc.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552749">WIA_PROPERTY_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549167">wiasCreatePropContext</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [image\image]:%20wiasUpdateScanRect function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
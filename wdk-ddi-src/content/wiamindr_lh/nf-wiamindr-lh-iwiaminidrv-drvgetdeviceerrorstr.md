---
UID: NF.wiamindr_lh.IWiaMiniDrv.drvGetDeviceErrorStr
title: IWiaMiniDrv::drvGetDeviceErrorStr
author: windows-driver-content
description: The IWiaMiniDrv::drvGetDeviceErrorStr method maps an error code to a Unicode string that describes the error.
old-location: image\iwiaminidrv_drvgetdeviceerrorstr.htm
ms.assetid: c34a6834-8875-400c-9634-6c2b9b68164f
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: image
req.header: wiamindr_lh.h
req.include-header: Wiamindr.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Me and in Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IWiaMiniDrv.drvGetDeviceErrorStr
req.alt-loc: wiamindr_lh.h
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
ms.keywords: IWiaMiniDrv, drvGetDeviceErrorStr, IWiaMiniDrv::drvGetDeviceErrorStr
req.iface: IWiaMiniDrv
req.product: Windows 10 or later.
---

# IWiaMiniDrv::drvGetDeviceErrorStr method



## -description
<p>The <b>IWiaMiniDrv::drvGetDeviceErrorStr </b>method maps an error code to a Unicode string that describes the error.</p>


## -syntax

````
HRESULT drvGetDeviceErrorStr(
  [in]            LONG     lFlags,
  [in]            LONG     lDevErrVal,
  [out, optional] LPOLESTR *ppszDevErrStr,
  [out]           LONG     *plDevErr
);
````


## -parameters
<dl>

### -param <i>lFlags</i> [in]

<dd>
<p>Is currently unused. </p>
</dd>

### -param <i>lDevErrVal</i> [in]

<dd>
<p>Specifies the device error value to be mapped to a string. A value of zero indicates that no error occurred.</p>
</dd>

### -param <i>ppszDevErrStr</i> [out, optional]

<dd>
<p>Points to a memory location that will receive the address of a string describing the error. </p>
</dd>

### -param <i>plDevErr</i> [out]

<dd>
<p>Points to a memory location that will receive a status code for this method. If this method returns S_OK, the value stored will be zero. Otherwise, a minidriver-specific error code will be stored at the location pointed to by this parameter.</p>
</dd>
</dl>

## -returns
<p>On success, the method should return S_OK and clear the device error value pointed to by <i>plDevErr</i>. If the minidriver does not fully implement this method, the method should return E_NOTIMPL. If the minidriver does not recognize the error value passed to this method, the method should return E_INVALIDARG. If the method fails, it should return a standard COM error code and place a minidriver-specific error code value in the memory pointed to by <i>plDevErr</i>.</p>

## -remarks
<p>To obtain an error string that describes a device-specific minidriver-generated error value, the WIA service calls the <b>IWiaMiniDrv::drvGetDeviceErrorStr</b> method. In response to this call, the minidriver should use <b>CoTaskMemAlloc</b> (described in the Microsoft Windows SDK documentation) to allocate memory that will contain a localized Unicode string corresponding to the error code passed to the minidriver. The WIA service (or an application) will free the memory. It is likely that an application will display the string, so it should be meaningful to an end user. The string should be loaded from a resource file, so that it can be localized into a variety of languages.</p>

<p>To obtain an error string that describes a device-specific minidriver-generated error value, the WIA service calls the <b>IWiaMiniDrv::drvGetDeviceErrorStr</b> method. In response to this call, the minidriver should use <b>CoTaskMemAlloc</b> (described in the Microsoft Windows SDK documentation) to allocate memory that will contain a localized Unicode string corresponding to the error code passed to the minidriver. The WIA service (or an application) will free the memory. It is likely that an application will display the string, so it should be meaningful to an end user. The string should be loaded from a resource file, so that it can be localized into a variety of languages.</p>

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
<p>Available in Windows Me and in Windows XP and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wiamindr_lh.h (include Wiamindr.h)</dt>
</dl>
</td>
</tr>
</table>
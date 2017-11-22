---
UID: NE.wwan._WWAN_CELLULAR_CLASS
title: WWAN_CELLULAR_CLASS
author: windows-driver-content
description: The WWAN_CELLULAR_CLASS enumeration lists the different classes of cellular technology that are supported by the MB device.
old-location: netvista\wwan_cellular_class.htm
ms.assetid: c49f40b8-feb4-4dfd-9a2b-c800f3b5343a
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_CELLULAR_CLASS
req.alt-loc: wwan.h
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
ms.keywords: WUDF_WORKITEM_CONFIG, WUDF_WORKITEM_CONFIG, *PWUDF_WORKITEM_CONFIG
req.iface: 
req.product: Windows 10 or later.
---

# WWAN_CELLULAR_CLASS enumeration



## -description
<p>The WWAN_CELLULAR_CLASS enumeration lists the different classes of cellular technology that are
  supported by the MB device.</p>


## -syntax

````
typedef enum _WWAN_CELLULAR_CLASS { 
  WwanCellularClassUnknown  = 0,
  WwanCellularClassGsm,
  WwanCellularClassCdma,
  WwanCellularClassMax
} WWAN_CELLULAR_CLASS, *PWWAN_CELLULAR_CLASS;
````


## -enum-fields
<dl>

### -field <a id="WwanCellularClassUnknown"></a><a id="wwancellularclassunknown"></a><a id="WWANCELLULARCLASSUNKNOWN"></a><b>WwanCellularClassUnknown</b>

<dd>
<p>The device uses an unknown cellular technology.</p>
</dd>

### -field <a id="WwanCellularClassGsm"></a><a id="wwancellularclassgsm"></a><a id="WWANCELLULARCLASSGSM"></a><b>WwanCellularClassGsm</b>

<dd>
<p>The device uses GSM-based technology.</p>
</dd>

### -field <a id="WwanCellularClassCdma"></a><a id="wwancellularclasscdma"></a><a id="WWANCELLULARCLASSCDMA"></a><b>WwanCellularClassCdma</b>

<dd>
<p>The device uses CDMA-based technology.</p>
</dd>

### -field <a id="WwanCellularClassMax"></a><a id="wwancellularclassmax"></a><a id="WWANCELLULARCLASSMAX"></a><b>WwanCellularClassMax</b>

<dd>
<p>The total number of supported cellular classes.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wwan.h (include Wwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571204">WWAN_DEVICE_CAPS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WWAN_CELLULAR_CLASS enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
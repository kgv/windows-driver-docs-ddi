---
UID: NS.rilapitypes.RILCALLINFO_V5
title: RILCALLINFO_V5
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilcallinfo_v5_2.htm
ms.assetid: a2cadee5-40e4-4044-b631-1824099e2fd7
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILCALLINFO_V5
req.alt-loc: rilapitypes.h
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
ms.keywords: RILCALLINFO_V5, RILCALLINFO_V5
req.iface: 
req.product: Windows 10 or later.
---

# RILCALLINFO_V5 structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILCALLINFO_V5 {
  DWORD                           cbSize;
  DWORD                           dwParams;
  DWORD                           dwExecutor;
  DWORD                           dwID;
  RILCALLINFODIRECTION            dwDirection;
  RILCALLINFOSTATUS               dwStatus;
  RILCALLTYPE                     dwType;
  RILCALLINFOMULTIPARTY           dwMultiparty;
  RILADDRESS                      raAddress;
  RILSUBADDRESS                   rsaSubAddress;
  WCHAR [MAXLENGTH_DESCRIPTION]   wszDescription;
  RILREMOTEPARTYINFOVALUE         dwNumberPresentationIndicator;
  RILREMOTEPARTYINFOVALUE         dwNamePresentationIndicator;
  DWORD                           dwFlags;
  RILCALLINFODISCONNECTINITIATOR  dwDisconnectInitiator;
  RILCALLINFODISCONNECTREASON     dwDisconnectReason;
  RILCALLDISCONNECTDETAILS        stDisconnectDetails;
  RILCALLMEDIAOFFERANSWERSET      rcmOfferAnswer;
  RILCALLHANDOVERSTATE            rchsHandoverState;
  RILCALLMODIFICATIONCAUSECODE    dwCallModificationCauseCode;
  RILCALLRTT                      stRTTInfo;
} RILCALLINFO_V5, RILCALLINFO_V5;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwExecutor</b>

<dd></dd>

### -field <b>dwID</b>

<dd></dd>

### -field <b>dwDirection</b>

<dd></dd>

### -field <b>dwStatus</b>

<dd></dd>

### -field <b>dwType</b>

<dd></dd>

### -field <b>dwMultiparty</b>

<dd></dd>

### -field <b>raAddress</b>

<dd></dd>

### -field <b>rsaSubAddress</b>

<dd></dd>

### -field <b>wszDescription</b>

<dd></dd>

### -field <b>dwNumberPresentationIndicator</b>

<dd></dd>

### -field <b>dwNamePresentationIndicator</b>

<dd></dd>

### -field <b>dwFlags</b>

<dd></dd>

### -field <b>dwDisconnectInitiator</b>

<dd></dd>

### -field <b>dwDisconnectReason</b>

<dd></dd>

### -field <b>stDisconnectDetails</b>

<dd></dd>

### -field <b>rcmOfferAnswer</b>

<dd></dd>

### -field <b>rchsHandoverState</b>

<dd></dd>

### -field <b>dwCallModificationCauseCode</b>

<dd></dd>

### -field <b>stRTTInfo</b>

<dd></dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Rilapitypes.h</dt>
</dl>
</td>
</tr>
</table>
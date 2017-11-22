---
UID: NC.bthddi.PFNBTHPORT_INDICATION_CALLBACK_ENHANCED
title: PFNBTHPORT_INDICATION_CALLBACK_ENHANCED
author: windows-driver-content
description: Profile drivers implement an enhanced L2CAP callback function to provide the Bluetooth driver stack with a mechanism to notify the profile driver about any changes to the status of a currently open L2CAP or eL2CAP connection.
old-location: bltooth\enhanced_l2cap_callback_function.htm
ms.assetid: 1C08937A-2B0C-4A6C-ACDF-1A751BF0D6F6
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthddi.h
req.include-header: Bthddi.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in Windows 8 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BluetoothPortIndicationCallbackEnhanced
req.alt-loc: bthddi.h
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
ms.keywords: IBidiSpl2, UnbindDevice, IBidiSpl2::UnbindDevice
req.iface: IBidiSpl2
---

# PFNBTHPORT_INDICATION_CALLBACK_ENHANCED callback



## -description
<p>Profile drivers implement an enhanced L2CAP callback function to provide the Bluetooth driver stack with a
  mechanism to notify the profile driver about any changes to the status of a currently open L2CAP or eL2CAP connection.</p>


## -prototype

````
PFNBTHPORT_INDICATION_CALLBACK_ENHANCED BluetoothPortIndicationCallbackEnhanced;

VOID WINAPI BluetoothPortIndicationCallbackEnhanced(
  _In_ PVOID                           Context,
  _In_ INDICATION_CODE                 Indication,
  _In_ PINDICATION_PARAMETERS_ENHANCED Parameters
)
{ ... }
````


## -parameters
<dl>

### -param <i>Context</i> [in]

<dd>
<p>For
     changes to existing L2CAP connections, this is the 
     <b>CallbackContext</b> member specified by the profile driver when it built and sent a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/hh450893">_BRB_L2CA_OPEN_ENHANCED_CHANNEL</a> structure.</p>
</dd>

### -param <i>Indication</i> [in]

<dd>
<p>An 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536679">INDICATION_CODE</a> value that indicates the type
     of L2CAP event.</p>
</dd>

### -param <i>Parameters</i> [in]

<dd>
<p>An 
     <a href="https://msdn.microsoft.com/library/windows/hardware/hh450875">INDICATION_PARAMETERS_ENHANCED</a> structure that
     contains event-specific parameters.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A profile driver registers its L2CAP or eL2CAP callback function by specifying the callback function in the 
      <b>Callback</b> member of the _BRB_L2CA_OPEN_ENHANCED_CHANNEL structure when the profile driver attempts to connect to a remote device using the
      BRB_L2CA_OPEN_ENHANCED_CHANNEL or BRB_L2CA_OPEN_ENHANCED_CHANNEL_RESPONSE BRBs.</p>

<p>After the profile driver registers its L2CAP callback function, the callback function is only
    associated with the enhanced channel that the BRB opened. The Bluetooth driver stack can call the L2CAP callback
    function to notify the profile driver of actions that occur over the open enhanced channel to the remote device.
    Profile drivers can register a single callback function to handle L2CAP channel notifications as a client.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/hh450875">INDICATION_PARAMETERS_ENHANCED</a> structure held in
    the 
    <i>Parameters</i> parameter is interpreted according to the value of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536679">INDICATION_CODE</a> enumeration that the Bluetooth
    driver stack passes to the profile driver's enhanced L2CAP callback function through the 
    <i>Indication</i> parameter. For most notifications, there is an INDICATION_PARAMETERS_ENHANCED union member that
    corresponds to the event and contains event-specific parameters.</p>

<p>A profile driver registers its L2CAP or eL2CAP callback function by specifying the callback function in the 
      <b>Callback</b> member of the _BRB_L2CA_OPEN_ENHANCED_CHANNEL structure when the profile driver attempts to connect to a remote device using the
      BRB_L2CA_OPEN_ENHANCED_CHANNEL or BRB_L2CA_OPEN_ENHANCED_CHANNEL_RESPONSE BRBs.</p>

<p>After the profile driver registers its L2CAP callback function, the callback function is only
    associated with the enhanced channel that the BRB opened. The Bluetooth driver stack can call the L2CAP callback
    function to notify the profile driver of actions that occur over the open enhanced channel to the remote device.
    Profile drivers can register a single callback function to handle L2CAP channel notifications as a client.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/hh450875">INDICATION_PARAMETERS_ENHANCED</a> structure held in
    the 
    <i>Parameters</i> parameter is interpreted according to the value of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536679">INDICATION_CODE</a> enumeration that the Bluetooth
    driver stack passes to the profile driver's enhanced L2CAP callback function through the 
    <i>Indication</i> parameter. For most notifications, there is an INDICATION_PARAMETERS_ENHANCED union member that
    corresponds to the event and contains event-specific parameters.</p>

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
<p>Supported in Windows 8 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Bthddi.h (include Bthddi.h)</dt>
</dl>
</td>
</tr>
</table>
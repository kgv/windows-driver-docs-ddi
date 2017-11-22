---
UID: NE.nfccx._NFC_CX_DRIVER_FLAGS
title: NFC_CX_DRIVER_FLAGS
author: windows-driver-content
description: Specifies run-time driver flags.
old-location: nfpdrivers\nfc_cx_driver_flags.htm
ms.assetid: 161CA2C2-F4F4-49F3-9007-ADFBDA905119
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: nfpdrivers
req.header: nfccx.h
req.include-header: Ncidef.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: None supported
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NFC_CX_DRIVER_FLAGS
req.alt-loc: nfccx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Requires same
ms.keywords: NPI_REGISTRATION_INSTANCE, NPI_REGISTRATION_INSTANCE
req.iface: 
---

# NFC_CX_DRIVER_FLAGS enumeration



## -description
<p>Specifies run-time driver flags.</p>


## -syntax

````
typedef enum _NFC_CX_DRIVER_FLAGS { 
  NFC_CX_DRIVER_DISABLE_WTD_TIMER                      = 0x00000001,
  NFC_CX_DRIVER_DISABLE_NFCEE_DISCOVERY                = 0x00000002,
  NFC_CX_DRIVER_DISABLE_RECOVERY_MODE                  = 0x00000004,
  NFC_CX_DRIVER_DISABLE_HOST_CARD_EMULATION            = 0x000000010,
  NFC_CX_DRIVER_HCI_NETWORK_PER_NFCEE                  = 0x000000020,
  NFC_CX_DRIVER_DISABLE_NFCEE_ACTION_NTF               = 0x000000040,
  NFC_CX_DRIVER_ENABLE_EEPROM_WRITE_PROTECTION         = 0x000000080,
  NFC_CX_DRIVER_ISODEP_RNAK_PRESENCE_CHK_SUPPORTED     = 0x000000100,
  NFC_CX_DRIVER_RF_ROUTING_POWER_SUB_STATES_SUPPORTED  = 0x000000200
} NFC_CX_DRIVER_FLAGS, *PNFC_CX_DRIVER_FLAGS;
````


## -enum-fields
<dl>

### -field <a id="NFC_CX_DRIVER_DISABLE_WTD_TIMER"></a><a id="nfc_cx_driver_disable_wtd_timer"></a><b>NFC_CX_DRIVER_DISABLE_WTD_TIMER</b>

<dd>
<p>Disable watchdog timer in CX.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_DISABLE_NFCEE_DISCOVERY"></a><a id="nfc_cx_driver_disable_nfcee_discovery"></a><b>NFC_CX_DRIVER_DISABLE_NFCEE_DISCOVERY</b>

<dd>
<p>Disable NFCEE discovery.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_DISABLE_RECOVERY_MODE"></a><a id="nfc_cx_driver_disable_recovery_mode"></a><b>NFC_CX_DRIVER_DISABLE_RECOVERY_MODE</b>

<dd>
<p>Disable NCI recovery mechanism in CX.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_DISABLE_HOST_CARD_EMULATION"></a><a id="nfc_cx_driver_disable_host_card_emulation"></a><b>NFC_CX_DRIVER_DISABLE_HOST_CARD_EMULATION</b>

<dd>
<p>Disable host card emulation feature.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_HCI_NETWORK_PER_NFCEE"></a><a id="nfc_cx_driver_hci_network_per_nfcee"></a><b>NFC_CX_DRIVER_HCI_NETWORK_PER_NFCEE</b>

<dd>
<p>NFCC implements a separate HCI network per NFCEE.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_DISABLE_NFCEE_ACTION_NTF"></a><a id="nfc_cx_driver_disable_nfcee_action_ntf"></a><b>NFC_CX_DRIVER_DISABLE_NFCEE_ACTION_NTF</b>

<dd>
<p>Disable NFCEE action notification.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_ENABLE_EEPROM_WRITE_PROTECTION"></a><a id="nfc_cx_driver_enable_eeprom_write_protection"></a><b>NFC_CX_DRIVER_ENABLE_EEPROM_WRITE_PROTECTION</b>

<dd>
<p>Enable opt to over-write only when configs change.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_ISODEP_RNAK_PRESENCE_CHK_SUPPORTED"></a><a id="nfc_cx_driver_isodep_rnak_presence_chk_supported"></a><b>NFC_CX_DRIVER_ISODEP_RNAK_PRESENCE_CHK_SUPPORTED</b>

<dd>
<p>The R-NAK command for ISO-DEP will be used for presence check.</p>
</dd>

### -field <a id="NFC_CX_DRIVER_RF_ROUTING_POWER_SUB_STATES_SUPPORTED"></a><a id="nfc_cx_driver_rf_routing_power_sub_states_supported"></a><b>NFC_CX_DRIVER_RF_ROUTING_POWER_SUB_STATES_SUPPORTED</b>

<dd>
<p>Indicates support for RF routing switched ON power sub-states.</p>
</dd>
</dl>

## -remarks
<p>The NFC CX allows the NFC client driver to provide some driver flags that can be used to configure the run-time implementation of the class extension. These flags enable the NFC CX to implement some standard NCI operations slightly differently to support different firmware implementations due to ambiguities in the NCI specification.</p>

<p>The NFC CX allows the NFC client driver to provide some driver flags that can be used to configure the run-time implementation of the class extension. These flags enable the NFC CX to implement some standard NCI operations slightly differently to support different firmware implementations due to ambiguities in the NCI specification.</p>

<p>The NFC CX allows the NFC client driver to provide some driver flags that can be used to configure the run-time implementation of the class extension. These flags enable the NFC CX to implement some standard NCI operations slightly differently to support different firmware implementations due to ambiguities in the NCI specification.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>None supported</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Nfccx.h (include Ncidef.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?LinkID=785320">Near field communication (NFC) design guide</a></dt>
<dt><a href="https://msdn.microsoft.com/windows/hardware/drivers/nfc/nfc-class-extension-">NFC class extension design guide</a></dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [nfpdrivers\nfpdrivers]:%20NFC_CX_DRIVER_FLAGS enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
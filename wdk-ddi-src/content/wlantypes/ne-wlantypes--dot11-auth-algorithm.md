---
UID: NE.wlantypes._DOT11_AUTH_ALGORITHM
title: DOT11_AUTH_ALGORITHM
author: windows-driver-content
description: Important  The Native 802.11 Wireless LAN interface is deprecated in Windows 10 and later.
old-location: netvista\dot11_auth_algorithm.htm
ms.assetid: 27bba553-2d46-4892-864a-52e44caf6d56
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: wlantypes.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating
   systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DOT11_AUTH_ALGORITHM
req.alt-loc: wlantypes.h
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
ms.keywords: DOT11_MSONEX_RESULT_PARAMS, DOT11_MSONEX_RESULT_PARAMS, *PDOT11_MSONEX_RESULT_PARAMS
req.iface: 
req.product: Windows 10 or later.
---

# DOT11_AUTH_ALGORITHM enumeration



## -description

## -syntax

````
typedef enum _DOT11_AUTH_ALGORITHM { 
  DOT11_AUTH_ALGO_80211_OPEN        = 1,
  DOT11_AUTH_ALGO_80211_SHARED_KEY  = 2,
  DOT11_AUTH_ALGO_WPA               = 3,
  DOT11_AUTH_ALGO_WPA_PSK           = 4,
  DOT11_AUTH_ALGO_WPA_NONE          = 5,
  DOT11_AUTH_ALGO_RSNA              = 6,
  DOT11_AUTH_ALGO_RSNA_PSK          = 7,
  DOT11_AUTH_ALGO_IHV_START         = 0x80000000,
  DOT11_AUTH_ALGO_IHV_END           = 0xffffffff
} DOT11_AUTH_ALGORITHM, *PDOT11_AUTH_ALGORITHM;
````


## -enum-fields
<dl>

### -field <a id="DOT11_AUTH_ALGO_80211_OPEN"></a><a id="dot11_auth_algo_80211_open"></a><b>DOT11_AUTH_ALGO_80211_OPEN</b>

<dd>
<p>
      Specifies an IEEE 802.11 Open System authentication algorithm.
     </p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_80211_SHARED_KEY"></a><a id="dot11_auth_algo_80211_shared_key"></a><b>DOT11_AUTH_ALGO_80211_SHARED_KEY</b>

<dd>
<p>Specifies an IEEE 802.11 Shared Key authentication algorithm that requires the use of a pre-shared
     Wired Equivalent Privacy (WEP) key for the 802.11 authentication.</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_WPA"></a><a id="dot11_auth_algo_wpa"></a><b>DOT11_AUTH_ALGO_WPA</b>

<dd>
<p>Specifies a Wi-Fi Protected Access (WPA) algorithm. IEEE 802.1X port authorization is performed by
     the supplicant, authenticator, and authentication server. Cipher keys are dynamically derived through
     the authentication process. 
     </p>
<p>This algorithm is valid only for basic service set (BSS) types of 
     dot11_BSS_type_infrastructure.</p>
<p>When the WPA algorithm is enabled, the 802.11 station associates only with an access point whose
     beacon or probe responses contain the authentication suite of type 1 (802.1X) within the WPA information
     element (IE).</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_WPA_PSK"></a><a id="dot11_auth_algo_wpa_psk"></a><b>DOT11_AUTH_ALGO_WPA_PSK</b>

<dd>
<p>Specifies a Wi-Fi Protected Access (WPA) algorithm that uses preshared keys (PSK). IEEE 802.1X
     port authorization is performed by the supplicant and authenticator. Cipher keys are dynamically derived
     through a preshared key that is used on both the supplicant and authenticator. 
     </p>
<p>This algorithm is valid only for BSS types of 
     dot11_BSS_type_infrastructure.</p>
<p>When the WPA PSK algorithm is enabled, the 802.11 station will associate only with an access point
     whose beacon or probe responses contain the authentication suite of type 2 (preshared key) within the
     WPA IE.</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_WPA_NONE"></a><a id="dot11_auth_algo_wpa_none"></a><b>DOT11_AUTH_ALGO_WPA_NONE</b>

<dd>
<p>This value is not supported.</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_RSNA"></a><a id="dot11_auth_algo_rsna"></a><b>DOT11_AUTH_ALGO_RSNA</b>

<dd>
<p>Specifies an IEEE 802.11i Robust Security Network Association (RSNA) algorithm. IEEE 802.1X port
     authorization is performed by the supplicant, authenticator, and authentication server. Cipher keys are
     dynamically derived through the authentication process.
     </p>
<p>This algorithm is valid only for BSS types of 
     dot11_BSS_type_infrastructure.</p>
<p>When the RSNA algorithm is enabled, the 802.11 station will associate only with an access point whose
     beacon or probe responses contain the authentication suite of type 1 (802.1X) within the Robust Security
     Network (RSN) IE.</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_RSNA_PSK"></a><a id="dot11_auth_algo_rsna_psk"></a><b>DOT11_AUTH_ALGO_RSNA_PSK</b>

<dd>
<p>Specifies an IEEE 802.11i RSNA algorithm that uses PSK. IEEE 802.1X port authorization is
     performed by the supplicant and authenticator. Cipher keys are dynamically derived through a pre-shared
     key that is used on both the supplicant and authenticator.
     </p>
<p>When the RSNA PSK algorithm is enabled, the 802.11 station will associate only with an access point
     whose beacon or probe responses contain the authentication suite of type 2 (preshared key) within the
     RSN IE.</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_IHV_START"></a><a id="dot11_auth_algo_ihv_start"></a><b>DOT11_AUTH_ALGO_IHV_START</b>

<dd>
<p>Specifies the start of the range that specifies proprietary authentication algorithms that are
     developed by an IHV.
     </p>
<p>The 
     DOT11_AUTH_ALGO_IHV_START enumerator is valid only when the miniport driver is operating in
     Extensible Station (ExtSTA) mode.</p>
</dd>

### -field <a id="DOT11_AUTH_ALGO_IHV_END"></a><a id="dot11_auth_algo_ihv_end"></a><b>DOT11_AUTH_ALGO_IHV_END</b>

<dd>
<p>Specifies the end of the range that specifies proprietary authentication algorithms that are
     developed by an IHV.
     </p>
<p>The 
     DOT11_AUTH_ALGO_IHV_END enumerator is valid only when the miniport driver is operating in ExtSTA
     mode.</p>
</dd>
</dl>

## -remarks
<p>An IHV can assign a value for its proprietary authentication algorithms from 
    DOT11_AUTH_ALGO_IHV_START through 
    DOT11_AUTH_ALGO_IHV_END. The IHV must assign a unique number from this range for each of its
    proprietary authentication algorithms.</p>

<p>If the IHV develops its own support for an authentication algorithm supported by the operating system,
    the IHV must also assign a unique number from this range. For example, if the IHV develops its own
    version of RSNA, it must assign a value for this version from 
    DOT11_AUTH_ALGO_IHV_START through 
    DOT11_AUTH_ALGO_IHV_END.</p>

<p>Starting with Windows 7, an 802.11 miniport driver can report any combination of supported
    authentication and cipher algorithm pairs in the 
    <a href="https://msdn.microsoft.com/e1440041-a7cd-45c6-8aa5-445d6de2bc20">
    DOT11_AUTH_CIPHER_PAIR_LIST</a> structure. However, if the operating system starts Soft AP, it enables
    only the 
    DOT11_AUTH_ALGO_RSNA_PSK authentication algorithm and the 
    DOT11_CIPHER_ALGO_CCMP cipher algorithm. To support Soft AP, the miniport driver must support this
    authentication/cipher pair.</p>

<p>If WPS is enabled on a NIC that is operating in Extensible AP mode, the miniport driver must allow
    peer stations to associate with the Extensible AP by using 
    <a href="NULL">Open System Authentication</a> or 
    <a href="https://msdn.microsoft.com/41dd280b-e54c-4233-8051-45e7b1284d1d">Wired Equivalent Privacy (WEP)</a> algorithms, regardless of
    the enabled authorization and cipher algorithms. For more information about WPS and Extensible AP, see 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff569436">OID_DOT11_WPS_ENABLED</a>.</p>

<p>An IHV can assign a value for its proprietary authentication algorithms from 
    DOT11_AUTH_ALGO_IHV_START through 
    DOT11_AUTH_ALGO_IHV_END. The IHV must assign a unique number from this range for each of its
    proprietary authentication algorithms.</p>

<p>If the IHV develops its own support for an authentication algorithm supported by the operating system,
    the IHV must also assign a unique number from this range. For example, if the IHV develops its own
    version of RSNA, it must assign a value for this version from 
    DOT11_AUTH_ALGO_IHV_START through 
    DOT11_AUTH_ALGO_IHV_END.</p>

<p>Starting with Windows 7, an 802.11 miniport driver can report any combination of supported
    authentication and cipher algorithm pairs in the 
    <a href="https://msdn.microsoft.com/e1440041-a7cd-45c6-8aa5-445d6de2bc20">
    DOT11_AUTH_CIPHER_PAIR_LIST</a> structure. However, if the operating system starts Soft AP, it enables
    only the 
    DOT11_AUTH_ALGO_RSNA_PSK authentication algorithm and the 
    DOT11_CIPHER_ALGO_CCMP cipher algorithm. To support Soft AP, the miniport driver must support this
    authentication/cipher pair.</p>

<p>If WPS is enabled on a NIC that is operating in Extensible AP mode, the miniport driver must allow
    peer stations to associate with the Extensible AP by using 
    <a href="NULL">Open System Authentication</a> or 
    <a href="https://msdn.microsoft.com/41dd280b-e54c-4233-8051-45e7b1284d1d">Wired Equivalent Privacy (WEP)</a> algorithms, regardless of
    the enabled authorization and cipher algorithms. For more information about WPS and Extensible AP, see 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff569436">OID_DOT11_WPS_ENABLED</a>.</p>

<p>An IHV can assign a value for its proprietary authentication algorithms from 
    DOT11_AUTH_ALGO_IHV_START through 
    DOT11_AUTH_ALGO_IHV_END. The IHV must assign a unique number from this range for each of its
    proprietary authentication algorithms.</p>

<p>If the IHV develops its own support for an authentication algorithm supported by the operating system,
    the IHV must also assign a unique number from this range. For example, if the IHV develops its own
    version of RSNA, it must assign a value for this version from 
    DOT11_AUTH_ALGO_IHV_START through 
    DOT11_AUTH_ALGO_IHV_END.</p>

<p>Starting with Windows 7, an 802.11 miniport driver can report any combination of supported
    authentication and cipher algorithm pairs in the 
    <a href="https://msdn.microsoft.com/e1440041-a7cd-45c6-8aa5-445d6de2bc20">
    DOT11_AUTH_CIPHER_PAIR_LIST</a> structure. However, if the operating system starts Soft AP, it enables
    only the 
    DOT11_AUTH_ALGO_RSNA_PSK authentication algorithm and the 
    DOT11_CIPHER_ALGO_CCMP cipher algorithm. To support Soft AP, the miniport driver must support this
    authentication/cipher pair.</p>

<p>If WPS is enabled on a NIC that is operating in Extensible AP mode, the miniport driver must allow
    peer stations to associate with the Extensible AP by using 
    <a href="NULL">Open System Authentication</a> or 
    <a href="https://msdn.microsoft.com/41dd280b-e54c-4233-8051-45e7b1284d1d">Wired Equivalent Privacy (WEP)</a> algorithms, regardless of
    the enabled authorization and cipher algorithms. For more information about WPS and Extensible AP, see 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff569436">OID_DOT11_WPS_ENABLED</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating
   systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wlantypes.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/770962e3-0339-46f8-a789-7c9bbf9e058f">
   DOT11_ASSOCIATION_COMPLETION_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547659">DOT11_AUTH_CIPHER_PAIR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547662">DOT11_AUTH_CIPHER_PAIR_LIST</a>
</dt>
<dt>
<a href="netvista.oid_dot11_enabled_authentication_algorithm">
   OID_DOT11_ENABLED_AUTHENTICATION_ALGORITHM</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20DOT11_AUTH_ALGORITHM enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
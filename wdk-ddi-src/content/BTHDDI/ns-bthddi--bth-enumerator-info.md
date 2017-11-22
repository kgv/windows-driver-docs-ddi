---
UID: NS.bthddi._BTH_ENUMERATOR_INFO
title: BTH_ENUMERATOR_INFO
author: windows-driver-content
description: The BTH_ENUMERATOR_INFO structure contains information about an underlying device and the service that caused the Plug and Play (PnP) manager to load the profile driver.
old-location: bltooth\bth_enumerator_info.htm
ms.assetid: e526d664-35cf-4738-9501-08298e90be1e
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthddi.h
req.include-header: Bthddi.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BTH_ENUMERATOR_INFO
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
req.irql: Developers should code this function to operate at either IRQL = DISPATCH_LEVEL (if the callback
   function does not access paged memory), or IRQL = PASSIVE_LEVEL (if the callback function must access
   paged memory)
ms.keywords: BTH_ENUMERATOR_INFO, BTH_ENUMERATOR_INFO, *PBTH_ENUMERATOR_INFO
req.iface: IBidiSpl2
---

# BTH_ENUMERATOR_INFO structure



## -description
<p>The BTH_ENUMERATOR_INFO structure contains information about an underlying device and the service
  that caused the Plug and Play (PnP) manager to load the profile driver.</p>


## -syntax

````
typedef struct _BTH_ENUMERATOR_INFO {
  ENUMERATOR_TYPE   EnumeratorType;
  ENUMERATOR_ACTION Action;
  ULONG             Port;
  ULONG             Flags;
  GUID              Guid;
  ULONG             InstanceId;
  WCHAR             InstanceIdStr[BTH_MAX_SERVICE_NAME_SIZE];
  USHORT            Vid;
  USHORT            Pid;
  USHORT            Mfg;
  USHORT            LocalMfg;
  USHORT            VidType;
  WCHAR             ServiceName[BTH_MAX_SERVICE_NAME_SIZE];
  CHAR              SdpPriLangServiceName[BTH_MAX_SERVICE_NAME_SIZE];
  WCHAR             DeviceString[BTH_MAX_SERVICE_NAME_SIZE];
} BTH_ENUMERATOR_INFO, *PBTH_ENUMERATOR_INFO;
````


## -struct-fields
<dl>

### -field <b>EnumeratorType</b>

<dd>
<p>Reserved for use by the Bluetooth driver stack. Do not use.</p>
</dd>

### -field <b>Action</b>

<dd>
<p>Reserved for use by the Bluetooth driver stack. Do not use.</p>
</dd>

### -field <b>Port</b>

<dd>
<p>If the enumeration was caused by a connection request, this member contains the device's port
     number. Otherwise, this value is undefined. For a L2CAP connection request, the port number also
     identifies the Protocol/Service Multiplexer (PSM) that is being connected to. For an RFCOMM connection
     request, this is an RFCOMM data link connection identifier (DLCI).</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>A flag that indicates the direction of the request. Possible values include:</p>
<ul>
<li>BTH_ENUMERATORFL_INCOMING</li>
<li>BTH_ENUMERATORFL_OUTGOING</li>
<li>BTH_ENUMERATORFL_REENUM</li>
</ul>
</dd>

### -field <b>Guid</b>

<dd>
<p>
      The enumeration protocol or service class GUID. This value is usually obtained from the INF file
      that loaded the profile driver.
     </p>
</dd>

### -field <b>InstanceId</b>

<dd>
<p>
      The instance ID of the protocol or service if the BTH_ENUMERATORFL_INCOMING flag is set.
     </p>
</dd>

### -field <b>InstanceIdStr</b>

<dd>
<p>
      The instance ID of the protocol or service if the BTH_ENUMERATORFL_OUTGOING flag is set.
     </p>
</dd>

### -field <b>Vid</b>

<dd>
<p>The vendor ID of the remote device, which is obtained from SDP.</p>
</dd>

### -field <b>Pid</b>

<dd>
<p>The product ID of the remote device, which is obtained from SDP.</p>
</dd>

### -field <b>Mfg</b>

<dd>
<p>The manufacturer ID of the remote device, which is obtained from SDP.</p>
</dd>

### -field <b>LocalMfg</b>

<dd>
<p>The local radio manufacturer obtained from the HCI.</p>
</dd>

### -field <b>VidType</b>

<dd>
<p>
      The remote device vendor ID type, which is obtained from SDP.
     </p>
</dd>

### -field <b>ServiceName</b>

<dd>
<p>The service name that is used for local services.</p>
</dd>

### -field <b>SdpPriLangServiceName</b>

<dd>
<p>The identifier used for remote services.</p>
</dd>

### -field <b>DeviceString</b>

<dd>
<p>The device string for the remote device.</p>
</dd>
</dl>

## -remarks
<p>The 
    <a href="https://msdn.microsoft.com/43cd8e6b-5710-4308-a7c4-fb6f14940977">
    IOCTL_INTERNAL_BTHENUM_GET_ENUMINFO</a> call's output buffer contains the information about an
    underlying device and the service that caused the Plug and Play (PnP) manager to load the profile
    driver.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Versions: Supported in Windows Vista, and later.</p>
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

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536678">ENUMERATOR_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d5acaec6-7b3b-4dd9-8901-f96b4e49149f">ENUMERATOR_ACTION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/43cd8e6b-5710-4308-a7c4-fb6f14940977">
   IOCTL_INTERNAL_BTHENUM_GET_ENUMINFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20BTH_ENUMERATOR_INFO structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
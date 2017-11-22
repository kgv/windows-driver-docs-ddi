---
UID: NS.ndis._NDIS_PROTOCOL_CO_CHARACTERISTICS
title: NDIS_PROTOCOL_CO_CHARACTERISTICS
author: windows-driver-content
description: The NDIS_PROTOCOL_CO_CHARACTERISTICS structure specifies CoNDIS entry points for CoNDIS protocol drivers.
old-location: netvista\ndis_protocol_co_characteristics.htm
ms.assetid: 855e3231-502c-4c6f-99f9-7ad85354ccd5
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_PROTOCOL_CO_CHARACTERISTICS
req.alt-loc: ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section
ms.keywords: NDIS_PROTOCOL_CO_CHARACTERISTICS, NDIS_PROTOCOL_CO_CHARACTERISTICS, *PNDIS_PROTOCOL_CO_CHARACTERISTICS
req.iface: 
---

# NDIS_PROTOCOL_CO_CHARACTERISTICS structure



## -description
<p>The NDIS_PROTOCOL_CO_CHARACTERISTICS structure specifies CoNDIS entry points for CoNDIS protocol
  drivers.</p>


## -syntax

````
typedef struct _NDIS_PROTOCOL_CO_CHARACTERISTICS {
  NDIS_OBJECT_HEADER                        Header;
  ULONG                                     Flags;
  CO_STATUS_HANDLER_EX                      CoStatusHandlerEx;
  CO_AF_REGISTER_NOTIFY_HANDLER             CoAfRegisterNotifyHandler;
  CO_RECEIVE_NET_BUFFER_LISTS_HANDLER       CoReceiveNetBufferListsHandler;
  CO_SEND_NET_BUFFER_LISTS_COMPLETE_HANDLER CoSendNetBufferListsCompleteHandler;
} NDIS_PROTOCOL_CO_CHARACTERISTICS, *PNDIS_PROTOCOL_CO_CHARACTERISTICS;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>The 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure for the
     protocol driver CoNDIS characteristics structure (NDIS_PROTOCOL_CO_CHARACTERISTICS). The driver sets the
     
     <b>Type</b> member of the structure that 
     <b>Header</b> specifies to NDIS_OBJECT_TYPE_CO_PROTOCOL_CHARACTERISTICS, the 
     <b>Revision</b> member to NDIS_PROTOCOL_CO_CHARACTERISTICS_REVISION_1, and the 
     <b>Size</b> member to NDIS_SIZEOF_PROTOCOL_CO_CHARACTERISTICS_REVISION_1.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Reserved for NDIS.</p>
</dd>

### -field <b>CoStatusHandlerEx</b>

<dd>
<p>The entry point of the driver's 
     <a href="https://msdn.microsoft.com/1416ad56-548c-4f12-9922-9ab9a7e4fd3a">ProtocolCoStatusEx</a> function.</p>
</dd>

### -field <b>CoAfRegisterNotifyHandler</b>

<dd>
<p>The entry point of the driver's 
     <a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">
     ProtocolCoAfRegisterNotify</a> function.</p>
</dd>

### -field <b>CoReceiveNetBufferListsHandler</b>

<dd>
<p>The entry point of the driver's 
     <a href="https://msdn.microsoft.com/1755804c-d82f-465d-862f-8a2340516f8e">
     ProtocolCoReceiveNetBufferLists</a> function.</p>
</dd>

### -field <b>CoSendNetBufferListsCompleteHandler</b>

<dd>
<p>The entry point of the driver's 
     <a href="https://msdn.microsoft.com/fb4b00c0-0b14-48dd-a6f2-aae659c6bb28">
     ProtocolCoSendNetBufferListsComplete</a> function.</p>
</dd>
</dl>

## -remarks
<p>To specify entry points for CoNDIS, a protocol driver initializes an NDIS_PROTOCOL_CO_CHARACTERISTICS
    structure and passes it to the 
    <a href="https://msdn.microsoft.com/97649f4f-942a-47fc-a541-6f160c8b4eb4">
    NdisSetOptionalHandlers</a> function.</p>

<p>The protocol driver calls 
    <b>NdisSetOptionalHandlers</b> from the 
    <a href="https://msdn.microsoft.com/342e23ad-d38b-4100-949a-220b8fbdcf6e">ProtocolSetOptions</a> function.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">ProtocolCoAfRegisterNotify</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1755804c-d82f-465d-862f-8a2340516f8e">
   ProtocolCoReceiveNetBufferLists</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/fb4b00c0-0b14-48dd-a6f2-aae659c6bb28">
   ProtocolCoSendNetBufferListsComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1416ad56-548c-4f12-9922-9ab9a7e4fd3a">ProtocolCoStatusEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/342e23ad-d38b-4100-949a-220b8fbdcf6e">ProtocolSetOptions</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_PROTOCOL_CO_CHARACTERISTICS structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
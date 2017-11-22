---
UID: NS.bthsdpddi._BTHDDI_SDP_PARSE_INTERFACE
title: BTHDDI_SDP_PARSE_INTERFACE
author: windows-driver-content
description: The BTHDDI_SDP_PARSE_INTERFACE structure provides functions for parsing SDP records.
old-location: bltooth\bthddi_sdp_parse_interface.htm
ms.assetid: bb8a1dd5-8207-4034-993e-eed49dc0f9c4
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthsdpddi.h
req.include-header: BthSdpddi.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BTHDDI_SDP_PARSE_INTERFACE
req.alt-loc: bthsdpddi.h
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
ms.keywords: BTHDDI_SDP_PARSE_INTERFACE, BTHDDI_SDP_PARSE_INTERFACE, *PBTHDDI_SDP_PARSE_INTERFACE
req.iface: 
---

# BTHDDI_SDP_PARSE_INTERFACE structure



## -description
<p>The BTHDDI_SDP_PARSE_INTERFACE structure provides functions for parsing SDP records.</p>


## -syntax

````
typedef struct _BTHDDI_SDP_PARSE_INTERFACE {
  INTERFACE            Interface;
  PVALIDATESTREAM      SdpValidateStream;
  PCONVERTSTREAMTOTREE SdpConvertStreamToTree;
  PCONVERTTREETOSTREAM SdpConvertTreeToStream;
  PFREETREE            SdpFreeTree;
  PBYTESWAPUUID128     SdpByteSwapUuid128;
  PBYTESWAPUINT128     SdpByteSwapUint128;
  PBYTESWAPUINT64      SdpByteSwapUint64;
  PRETRIEVEUUID128     SdpRetrieveUuid128;
  PRETRIEVEUINT128     SdpRetrieveUint128;
  PRETRIEVEUINT64      SdpRetrieveUint64;
  PFINDATTRIBUTEINTREE SdpFindAttributeInTree;
  PGETNEXTELEMENT      SdpGetNextElement;
  pReservedFunction    Reserved1;
  pReservedFunction    Reserved2;
  pReservedFunction    Reserved3;
  pReservedFunction    Reserved4;
} BTHDDI_SDP_PARSE_INTERFACE, *PBTHDDI_SDP_PARSE_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>Interface</b>

<dd>
<p>A structure that describes the 
     <b>BTHDDI_SDP_NODE_INTERFACE</b> interface for use by profile drivers. For more information about this
     structure, see 
     <a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a>.</p>
</dd>

### -field <b>SdpValidateStream</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536847">SdpValidateStream</a> function.</p>
</dd>

### -field <b>SdpConvertStreamToTree</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/3b285a32-c1bc-4103-aa2e-0f6c8f5cc7ec">
     SdpConvertStreamToTree</a> function.</p>
</dd>

### -field <b>SdpConvertTreeToStream</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/6e3cc0ae-e214-4096-834b-b435ee0fcb46">
     SdpConvertTreeToStream</a> function.</p>
</dd>

### -field <b>SdpFreeTree</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536839">SdpFreeTree</a> function.</p>
</dd>

### -field <b>SdpByteSwapUuid128</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536793">SdpByteSwapUuid128</a> function.</p>
</dd>

### -field <b>SdpByteSwapUint128</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536788">SdpByteSwapUint128</a> function.</p>
</dd>

### -field <b>SdpByteSwapUint64</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536790">SdpByteSwapUint64</a> function.</p>
</dd>

### -field <b>SdpRetrieveUuid128</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536846">SdpRetrieveUuid128</a> function.</p>
</dd>

### -field <b>SdpRetrieveUint128</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536843">SdpRetrieveUint128</a> function.</p>
</dd>

### -field <b>SdpRetrieveUint64</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536845">SdpRetrieveUint64</a> function.</p>
</dd>

### -field <b>SdpFindAttributeInTree</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/26c71c08-3b9a-474f-a232-d7f675582d27">
     SdpFindAttributeInTree</a> function.</p>
</dd>

### -field <b>SdpGetNextElement</b>

<dd>
<p>A pointer to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536841">SdpGetNextElement</a> function.</p>
</dd>

### -field <b>Reserved1</b>

<dd>
<p>Reserved for future use. Do not use.</p>
</dd>

### -field <b>Reserved2</b>

<dd>
<p>Reserved for future use. Do not use.</p>
</dd>

### -field <b>Reserved3</b>

<dd>
<p>Reserved for future use. Do not use.</p>
</dd>

### -field <b>Reserved4</b>

<dd>
<p>Reserved for future use. Do not use.</p>
</dd>
</dl>

## -remarks
<p>Profile drivers should specify the 
    <b>GUID_BTHDDI_SDP_PARSE_INTERFACE</b> GUID to query for an instance of the BTHDDI_SDP_PARSE_INTERFACE
    structure from the Bluetooth driver stack.</p>

<p>All the members of this structure, other than the 
    <b>Interface</b> member, are function pointers.</p>

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
<dt>Bthsdpddi.h (include BthSdpddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536847">SdpValidateStream</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536794">SdpConvertStreamToTree</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536796">SdpConvertTreeToStream</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536839">SdpFreeTree</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536793">SdpByteSwapUuid128</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536788">SdpByteSwapUint128</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536790">SdpByteSwapUint64</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536846">SdpRetrieveUuid128</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536843">SdpRetrieveUint128</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536845">SdpRetrieveUint64</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536838">SdpFindAttributeInTree</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536841">SdpGetNextElement</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20BTHDDI_SDP_PARSE_INTERFACE structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
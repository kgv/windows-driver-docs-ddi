---
UID: NE.sddef.SD_RESPONSE_TYPE
title: SD_RESPONSE_TYPE
author: windows-driver-content
description: The SD_RESPONSE_TYPE enumeration lists the types of response data that a Secure Digital (SD) card returns in response to a command.
old-location: sd\sd_response_type.htm
ms.assetid: 0a468158-4beb-42e0-a990-0282041a6bf8
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: SD
req.header: sddef.h
req.include-header: Sddef.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SD_RESPONSE_TYPE
req.alt-loc: sddef.h
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
ms.keywords: PSCSIWMIGUIDREGINFO, SCSIWMIGUIDREGINFO, *PSCSIWMIGUIDREGINFO
req.iface: 
req.product: Windows 10 or later.
---

# SD_RESPONSE_TYPE enumeration



## -description
<p>The SD_RESPONSE_TYPE enumeration lists the types of response data that a Secure Digital (SD) card returns in response to a command.</p>


## -syntax

````
typedef enum  { 
  SDRT_UNSPECIFIED  = 0,
  SDRT_NONE         = 1,
  SDRT_1            = 2,
  SDRT_1B           = 3,
  SDRT_2            = 4,
  SDRT_3            = 5,
  SDRT_4            = 6,
  SDRT_5            = 7,
  SDRT_5B           = 8,
  SDRT_6            = 9
} SD_RESPONSE_TYPE;
````


## -enum-fields
<dl>

### -field <a id="SDRT_UNSPECIFIED"></a><a id="sdrt_unspecified"></a><b>SDRT_UNSPECIFIED</b>

<dd>
<p>Indicates that the response from the card is unspecified.</p>
</dd>

### -field <a id="SDRT_NONE"></a><a id="sdrt_none"></a><b>SDRT_NONE</b>

<dd>
<p>Indicates that the command does not require a response from the card.</p>
</dd>

### -field <a id="SDRT_1"></a><a id="sdrt_1"></a><b>SDRT_1</b>

<dd>
<p>Indicates a response of type R1 that contains 32 bits of card status information. For an explanation of the R1 response, see the <i>SD Card Association</i> specification.</p>
</dd>

### -field <a id="SDRT_1B"></a><a id="sdrt_1b"></a><b>SDRT_1B</b>

<dd>
<p>Indicates a response of type R1b that is identical to R1 with an optional busy signal transmitted on the data line. For an explanation of the R1b response, see the <i>SD Card Association </i>specification.</p>
</dd>

### -field <a id="SDRT_2"></a><a id="sdrt_2"></a><b>SDRT_2</b>

<dd>
<p>Indicates a response of type R2 that contains either the contents of the Card Identification Register (CID) or the contents of the Card Specific Data Register (CSD), depending on which command provoked the response. For an explanation of the R2 response, see the <i>SD Card Association </i>specification. </p>
</dd>

### -field <a id="SDRT_3"></a><a id="sdrt_3"></a><b>SDRT_3</b>

<dd>
<p>Indicates a response of type R3 that contains the contents of the operating condition register (OCR). For an explanation of the R3 response, see the <i>SD Card Association </i>specification.</p>
</dd>

### -field <a id="SDRT_4"></a><a id="sdrt_4"></a><b>SDRT_4</b>

<dd>
<p>Indicates a response of type R4 that contains the contents of the relative card address register. For an explanation of the R4 response, see the <i>SD Card Association </i>specification.</p>
</dd>

### -field <a id="SDRT_5"></a><a id="sdrt_5"></a><b>SDRT_5</b>

<dd>
<p>Indicates a response of type R5 that the card uses to notify the host of an interrupt request. If the host itself generates the interrupt request, the RCA field is 0x0. For an explanation of the R5 response, see the <i>SD Card Association </i>specification.</p>
</dd>

### -field <a id="SDRT_5B"></a><a id="sdrt_5b"></a><b>SDRT_5B</b>

<dd>
<p>Indicates a response of type R5b. For an explanation of the R5b response, see the <i>SD Card Association </i>specification.</p>
</dd>

### -field <a id="SDRT_6"></a><a id="sdrt_6"></a><b>SDRT_6</b>

<dd>
<p>Indicates a response of type R6. For an explanation of the R6 response, see the <i>SD Card Association </i>specification.</p>
</dd>
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
<dt>Sddef.h (include Sddef.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/7c49c394-d0b3-4594-a623-0a13825bdcec">SDCMD_DESCRIPTOR</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [SD\buses]:%20SD_RESPONSE_TYPE enumeration%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
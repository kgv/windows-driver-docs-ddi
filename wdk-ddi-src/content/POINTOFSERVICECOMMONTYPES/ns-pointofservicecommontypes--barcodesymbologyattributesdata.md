---
UID: NS.pointofservicecommontypes._BarcodeSymbologyAttributesData
title: BarcodeSymbologyAttributesData
author: windows-driver-content
description: The BarcodeSymbologyAttributesData structure contains the attribute information for a barcode symbology.
old-location: pos\barcodesymbologyattributesdata.htm
ms.assetid: 0682B3AA-13F5-4686-AD78-D45DA85398B7
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: pos
req.header: pointofservicecommontypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BarcodeSymbologyAttributesData
req.alt-loc: pointofservicecommontypes.h
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
ms.keywords: BarcodeSymbologyAttributesData, BarcodeSymbologyAttributesData
req.iface: 
---

# BarcodeSymbologyAttributesData structure



## -description
<p>The <b>BarcodeSymbologyAttributesData</b> structure contains the attribute information  for a barcode symbology.</p>


## -syntax

````
typedef struct _BarcodeSymbologyAttributesData {
  BarcodeSymbology                 Symbology;
  UINT32                           IsCheckDigitValidationSupported;
  UINT32                           IsCheckDigitValidationEnabled;
  UINT32                           IsCheckDigitTransmissionSupported;
  UINT32                           IsCheckDigitTransmissionEnabled;
  UINT32                           IsDecodeLengthSupported;
  BarcodeSymbologyDecodeLengthType DecodeLengthType;
  UINT32                           DecodeLength1;
  UINT32                           DecodeLength2;
} BarcodeSymbologyAttributesData;
````


## -struct-fields
<dl>

### -field <b>Symbology</b>

<dd>
<p>The barcode symbology  to set or get attributes to or from.</p>
<p>For more information, see the <a href="https://msdn.microsoft.com/library/windows/hardware/dn757474">BarcodeSymbology</a> enumeration topic.</p>
</dd>

### -field <b>IsCheckDigitValidationSupported</b>

<dd>
<p>Indicates whether the barcode scanner supports check digit of the symbology. Non-zero if supported.</p>
</dd>

### -field <b>IsCheckDigitValidationEnabled</b>

<dd>
<p>Indicates whether the target barcodes are expected to contain a check digit.</p>
<p>Some barcodes may have the last digit as a validation digit to ensure  decoding accuracy.  Barcode scanners may choose to support the feature or not. Non-zero if enabled.</p>
</dd>

### -field <b>IsCheckDigitTransmissionSupported</b>

<dd>
<p>Indicates whether the barcode scanner supports check digit transmission. Non-zero if supported.</p>
</dd>

### -field <b>IsCheckDigitTransmissionEnabled</b>

<dd>
<p>Indicates whether the check digit is transmitted along with the decoded data. Non-zero if enabled.</p>
</dd>

### -field <b>IsDecodeLengthSupported</b>

<dd>
<p>Indicates whether the barcode scanner supports setting decode length for the symbology.</p>
<p>For example, the API can be used to set to read barcodes of decode length between 2 and 8.  This helps with filtering the target barcodes. Non-zero if supported.</p>
</dd>

### -field <b>DecodeLengthType</b>

<dd>
<p> The decode length type, which can be set to support a range, two discrete values, or be set to any length.
 For more information, see the <a href="https://msdn.microsoft.com/155D1C71-7935-4512-8AA2-0EB167FCBF5E">BarcodeSymbologyDecodeLengthType</a>.</p>
</dd>

### -field <b>DecodeLength1</b>

<dd>
<p>The first  value in a range, or the  first  discrete value.</p>
</dd>

### -field <b>DecodeLength2</b>

<dd>
<p>The last value in a range, or a second discrete value.</p>
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
<dt>Pointofservicecommontypes.h</dt>
</dl>
</td>
</tr>
</table>
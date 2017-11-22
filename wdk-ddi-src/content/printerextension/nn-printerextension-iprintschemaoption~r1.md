---
UID: NN.printerextension.IPrintSchemaOption~r1
title: IPrintSchemaOption
author: windows-driver-content
description: Exposes a Print Schema Option object.
old-location: print\iprintschemaoption_interface.htm
ms.assetid: B520875A-7882-43D5-A890-0F82654EFD6C
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: interface
ms.prod: windows-hardware
ms.technology: print
req.header: printerextension.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPrintSchemaOption
req.alt-loc: Printerextension.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: IPrintSchemaTicket2, GetParameterInitializer, IPrintSchemaTicket2::GetParameterInitializer
req.iface: IPrintSchemaTicket2
req.product: Windows 10 or later.
---

# IPrintSchemaOption interface



## -description
<p>Exposes a Print Schema Option object.</p>


## -inheritance
<p>The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IPrintSchemaOption</b> interface inherits from <a href="https://msdn.microsoft.com/library/windows/hardware/hh451262">IPrintSchemaDisplayableElement</a>. <b>IPrintSchemaOption</b> also has these types of members:</p>

<p>The <b>IPrintSchemaOption</b> interface has these methods.</p>

<p>Gets the XML node for the "value" child element of a "Property"  or a "ScoredProperty" element with the given name.</p>

<p> </p>

<p>The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IPrintSchemaOption</b> interface has these properties.</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh973227">Constrained</a>
</p>

<p>Read-only</p>

<p>Gets  the constraint setting type for the schema option.</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh973228">Selected</a>
</p>

<p>Read-only</p>

<p>Indicates whether this option is selected.</p>

<p> </p>

## -members
<p>The <b>IPrintSchemaOption</b> interface has these methods.</p><table class="members" id="memberListMethods">
<tr>
<th align="left" width="37%">Method</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451321">GetPropertyValue</a>
</td>
<td align="left" width="63%">
<p>Gets the XML node for the "value" child element of a "Property"  or a "ScoredProperty" element with the given name.</p>
</td>
</tr>
</table><p>Gets the XML node for the "value" child element of a "Property"  or a "ScoredProperty" element with the given name.</p>

<p> </p>

<p>The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IPrintSchemaOption</b> interface has these properties.</p><table class="members" id="memberListProperties">
<tr>
<th align="left" width="27%">Property</th>
<th align="left" width="10%">Access type</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="27%" xml:space="preserve">
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh973227">Constrained</a>
</p>
</td>
<td align="left" width="10%">
<p>Read-only</p>
</td>
<td align="left" width="63%">
<p>Gets  the constraint setting type for the schema option.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="27%" xml:space="preserve">
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh973228">Selected</a>
</p>
</td>
<td align="left" width="10%">
<p>Read-only</p>
</td>
<td align="left" width="63%">
<p>Indicates whether this option is selected.</p>
</td>
</tr>
</table><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh973227">Constrained</a>
</p>

<p>Read-only</p>

<p>Gets  the constraint setting type for the schema option.</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh973228">Selected</a>
</p>

<p>Read-only</p>

<p>Indicates whether this option is selected.</p>

<p> </p>

## -remarks
<p>You must ensure that each Feature or Option in a PrintTicket or PrintCapabilities XML document has a <i>name</i> attribute specified. This attribute is used to build the <b>IPrintSchemaOption</b> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451284">IPrintSchemaFeature</a> objects. If the <i>name</i> attribute is omitted, the feature or option will not be displayed in the object model, or the Microsoft-provided print preferences experience.</p>

<p>You must ensure that each Feature or Option in a PrintTicket or PrintCapabilities XML document has a <i>name</i> attribute specified. This attribute is used to build the <b>IPrintSchemaOption</b> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451284">IPrintSchemaFeature</a> objects. If the <i>name</i> attribute is omitted, the feature or option will not be displayed in the object model, or the Microsoft-provided print preferences experience.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Printerextension.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451262">IPrintSchemaDisplayableElement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/C9C4E085-1F2A-4610-AF2A-8F87E5CE7BCA">IPrintSchemaFeature::GetOption</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/C22BC037-05D2-4F44-8704-D1D56909B603">IPrintSchemaFeature::SelectedOption</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh846198">IPrintSchemaOptionCollection</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451378">IPrintSchemaPageMediaSizeOption</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IPrintSchemaOption interface%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.extsfns.IDebugFAEntryTags.GetProperties
title: IDebugFAEntryTags::GetProperties
author: windows-driver-content
description: The GetProperties method gets the name or description (or both) of a tag in a DebugFailureAnalysisTags object.
old-location: debugger\idebugfaentrytags_getproperties.htm
ms.assetid: 140EAE7D-E349-4096-8578-6CF011C1FBA7
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: extsfns.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugFAEntryTags.GetProperties
req.alt-loc: extsfns.h
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
ms.keywords: IDebugFAEntryTags, GetProperties, IDebugFAEntryTags::GetProperties
req.iface: IDebugFAEntryTags
---

# IDebugFAEntryTags::GetProperties method



## -description
<p>The <b>GetProperties</b> method gets the name or description (or both) of a tag in a <a href="https://msdn.microsoft.com/B52DFB0E-0035-40C2-B2F5-5E16B16931C2">DebugFailureAnalysisTags</a> object.</p>


## -syntax

````
HRESULT GetProperties(
            FA_TAG  Tag,
  [out]     PSTR    Name,
  [in, out] PULONG  NameSize,
  [out]     PSTR    Description,
  [in, out] PULONG  DescSize,
  [out]     PULONG  Flags
);
````


## -parameters
<dl>

### -param <i>Tag</i> 

<dd>
<p>A value in the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991810">FA_TAG</a> enumeration. This method gets the name or description (or both) of this tag.</p>
</dd>

### -param <i>Name</i> [out]

<dd>
<p>A pointer to a buffer that receives a null-terminated string that is the name of the tag. If <i>NameSize</i> is less than the length of the tag's name, this method copies only <i>NameSize</i> bytes, including the <b>NULL</b> terminator, to this buffer.</p>
</dd>

### -param <i>NameSize</i> [in, out]

<dd>
<p>On input, this parameter, specifies the size, in bytes, of the buffer pointed to by <i>Name</i>. On output, this parameter receives the size, in bytes, of the name of the tag. If the tag has no name, this parameter receives a value of 0.</p>
<div class="alert"><b>Note</b>  If <i>Name</i> is NULL, this parameter receives no information. You should either set both <i>Name</i> and <i>NameSize</i> to non-NULL values or set them both to <b>NULL</b>.</div>
<div> </div>
</dd>

### -param <i>Description</i> [out]

<dd>
<p>A pointer to a buffer that receives a null-terminated string that is the description of the tag. If <i>DescSize</i> is less than the length of the tag's description, this method copies only <i>DescSize</i> bytes, including the <b>NULL</b> terminator, to this buffer.</p>
</dd>

### -param <i>DescSize</i> [in, out]

<dd>
<p>On input, this parameter, specifies the size, in bytes, of the buffer pointed to by <i>Description</i>. On output, this parameter receives the size, in bytes, of the description of the tag. If the tag has no description, this parameter receives a value of 0.</p>
<div class="alert"><b>Note</b>  If <i>Description</i> is NULL, this parameter receives no information. You should either set both <i>Description</i> and <i>DescSize</i> to non-NULL values or set them both to <b>NULL</b>.</div>
<div> </div>
</dd>

### -param <i>Flags</i> [out]

<dd>
<p>Reserved. Set this parameter to NULL.</p>
</dd>
</dl>

## -returns
<p>The <b>HRESULT</b> values returned by this method are defined in winerror.h and strsafe.h. The values returned by this method include, but are not limited to the following:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>This method successfully retrieved the requested name or description  (or both), and no truncation of the requested string or strings was required.</p><dl>
<dt><b>STRSAFE_E_INSUFFICIENT_BUFFER</b></dt>
</dl><p>This method retrieved the requested name or description (or both), but the name or description was truncated.</p><dl>
<dt><b>STRSAFE_E_INVALID_PARAMETER </b></dt>
</dl><p>The caller passed at least one invalid parameter.</p>

<p> </p>

## -remarks


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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Extsfns.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983404">IDebugFAEntryTags</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983405">IDebugFailureAnalysis2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7648F789-85D5-4247-90DD-2EAA43543483">Writing an Analysis Extension Plug-in to Extend !analyze</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj991815">SetProperties</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983432">_EFN_Analyze</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugFAEntryTags::GetProperties method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
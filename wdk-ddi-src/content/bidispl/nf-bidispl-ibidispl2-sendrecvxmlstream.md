---
UID: NF.bidispl.IBidiSpl2.SendRecvXMLStream
title: IBidiSpl2::SendRecvXMLStream
author: windows-driver-content
description: The IBidiSpl2::SendRecvXMLStream method sends a bidirectional printer communication request and receives the response as IStream objects formatted in accordance with the Bidirectional Communication Schemas.
old-location: print\ibidispl2_ibidispl2__sendrecvxmlstream.htm
ms.assetid: 2daf99a8-42dc-4739-8e7e-80d3c9a084b7
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: bidispl.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Windows Vista
req.target-min-winversvr: Windows Server 2008
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IBidiSpl2.IBidiSpl2::SendRecvXMLStream
req.alt-loc: bidispl.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: Bidispl.dll
req.irql: PASSIVE_LEVEL
ms.keywords: IBidiSpl2, SendRecvXMLStream, IBidiSpl2::SendRecvXMLStream
req.iface: IBidiSpl2
---

# IBidiSpl2::SendRecvXMLStream method



## -description
<p>The <b>IBidiSpl2::SendRecvXMLStream</b> method sends a bidirectional printer communication request and receives the response as <a href="stg.istream">IStream</a> objects formatted in accordance with the <a href="https://msdn.microsoft.com/b15b1aff-623e-4159-ab0f-ce386a1377eb">Bidirectional Communication Schemas</a>.</p>


## -syntax

````
HRESULT IBidiSpl2::SendRecvXMLStream(
  [in]  IStream *pSRequest,
  [out] IStream **ppSResponse
);
````


## -parameters
<dl>

### -param <i>pSRequest</i> [in]

<dd>
<p>A pointer to the bidi communication request as a stream that complies with one of the <a href="https://msdn.microsoft.com/b15b1aff-623e-4159-ab0f-ce386a1377eb">Bidirectional Communication Schemas</a>.</p>
</dd>

### -param <i>ppSResponse</i> [out]

<dd>
<p>A pointer to the printer's response as a stream that complies with one of the <a href="https://msdn.microsoft.com/b15b1aff-623e-4159-ab0f-ce386a1377eb">Bidirectional Communication Schemas</a>.</p>
</dd>
</dl>

## -returns
<p>The method returns one of the following values.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The operation was successful.</p><dl>
<dt><b>E_HANDLE</b></dt>
</dl><p>The interface handle is invalid.</p><dl>
<dt><b>None of the above</b></dt>
</dl><p>The <b>HRESULT</b> contains an error code that corresponds to the last error.</p>

<p> </p>

<p>Note that the <b>HRESULT</b> may contain a system error code that is defined in <a href="https://msdn.microsoft.com/e273f5eb-e4f4-4aa7-9ed9-b418eebc6144">Bidi Error Codes</a>.</p>

## -remarks
<p>The character encoding of <i>ppSResponse</i> is UTF-8. The character encoding of <i>pSRequest</i> is either UTF-8 or Unicode with a byte order mark OxFEFF.</p>

<p>The character encoding of <i>ppSResponse</i> is UTF-8. The character encoding of <i>pSRequest</i> is either UTF-8 or Unicode with a byte order mark OxFEFF.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows Vista</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2008</p>
</td>
</tr>
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
<dt>Bidispl.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Bidispl.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dd144981">IBidiSpl2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545163">Bidirectional Communication Interfaces</a>
</dt>
<dt>
<a href="NULL">Bidirectional Communication Schema</a>
</dt>
<dt>
<a href="NULL">Print Spooler Components</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IBidiSpl2::IBidiSpl2::SendRecvXMLStream method%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
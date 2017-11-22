---
UID: NS.sdpnode._SDP_TREE_ROOT_NODE
title: SDP_TREE_ROOT_NODE
author: windows-driver-content
description: The SDP_TREE_ROOT_NODE structure is the root element of a tree-based representation of an SDP record.
old-location: bltooth\sdp_tree_root_node.htm
ms.assetid: bde75364-387b-4f57-8942-1cf32652c02d
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: bltooth
req.header: sdpnode.h
req.include-header: Sdpnode.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SDP_TREE_ROOT_NODE
req.alt-loc: sdpnode.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= PASSIVE_LEVEL
ms.keywords: SDP_TREE_ROOT_NODE, SDP_TREE_ROOT_NODE, *PSDP_TREE_ROOT_NODE
req.iface: 
req.product: Windows 10 or later.
---

# SDP_TREE_ROOT_NODE structure



## -description
<p>The SDP_TREE_ROOT_NODE structure is the root element of a tree-based representation of an SDP
  record.</p>


## -syntax

````
typedef struct _SDP_TREE_ROOT_NODE {
  SDP_NODE RootNode;
} SDP_TREE_ROOT_NODE, *PSDP_TREE_ROOT_NODE;
````


## -struct-fields
<dl>

### -field <b>RootNode</b>

<dd>
<p>An 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536848">SDP_NODE</a> structure that represents the root node of
     a tree-based representation of an SDP record.</p>
</dd>
</dl>

## -remarks
<p>Several SDP functions access or output this structure when they build a tree-based SDP record or
    convert a raw SDP record stream into a tree-based record.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536784">SdpAddAttributeToTree</a> function adds
    an SDP_NODE structure that contains SDP attribute information to an existing SDP_TREE_ROOT_NODE
    structure.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536794">SdpConvertStreamToTree</a> function
    outputs this structure as the root element of an SDP record that it converts from a stream to a
    tree-based structure.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536796">SdpConvertTreeToStream</a> function uses
    an existing SDP_TREE_ROOT_NODE structure as input when it converts a tree-based representation of an SDP
    record into a stream.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536818">SdpCreateNodeTree</a> function creates an
    empty SDP_TREE_ROOT_NODE structure. This is the first step in creating an SDP record as a tree. After the
    SDP tree is completed, a profile driver that is using SDP to advertise its service can convert the tree
    into an SDP record stream using the 
    <b>SdpConvertTreeToStream</b> function.</p>

<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536838">SdpFindAttributeInTree</a> function
    searches a populated SDP_TREE_ROOT_NODE structure for an SDP attribute value.</p>

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
<dt>Sdpnode.h (include Sdpnode.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536848">SDP_NODE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536784">SdpAddAttributeToTree</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536794">SdpConvertStreamToTree</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536796">SdpConvertTreeToStream</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536818">SdpCreateNodeTree</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536838">SdpFindAttributeInTree</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20SDP_TREE_ROOT_NODE structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
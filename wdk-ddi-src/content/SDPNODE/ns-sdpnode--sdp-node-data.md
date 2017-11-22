---
UID: NS.sdpnode._SDP_NODE_DATA
title: SDP_NODE_DATA
author: windows-driver-content
description: The SDP_NODE_DATA union holds the data of an element in a tree-based representation of an SDP record.
old-location: bltooth\sdp_node_data.htm
ms.assetid: ce1f9f1b-2215-4b39-b5e6-a5076f02af64
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
req.alt-api: SDP_NODE_DATA
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
ms.keywords: SDP_NODE_DATA, SDP_NODE_DATA, *PSDP_NODE_DATA
req.iface: 
req.product: Windows 10 or later.
---

# SDP_NODE_DATA structure



## -description
<p>The SDP_NODE_DATA union holds the data of an element in a tree-based representation of an SDP
  record.</p>


## -syntax

````
typedef union _SDP_NODE_DATA {
  SDP_LARGE_INTEGER_16  int128;
  SDP_ULARGE_INTEGER_16 uint128;
  GUID                  uuid128;
  ULONG                 uuid32;
  USHORT                uuid16;
  LONGLONG              int64;
  ULONGLONG             uint64;
  LONG                  int32;
  ULONG                 uint32;
  SHORT                 int16;
  USHORT                uint16;
  CHAR                  int8;
  UCHAR                 uint8;
  SDP_BOOLEAN           boolean;
  PCHAR                 string;
  PCHAR                 url;
  SDP_NODE_HEADER       sequence;
  SDP_NODE_HEADER       alternative;
  ISdpNodeContainer     *container;
  struct {
    PUCHAR stream;
    ULONG  streamLength;
  };
} SDP_NODE_DATA, *PSDP_NODE_DATA;
````


## -struct-fields
<dl>

### -field <b>int128</b>

<dd>
<p>The union member for a 128-bit integer.</p>
</dd>

### -field <b>uint128</b>

<dd>
<p>The union member for an unsigned 128-bit integer.</p>
</dd>

### -field <b>uuid128</b>

<dd>
<p>The union member for a 128-bit universally unique identifier (UUID).</p>
</dd>

### -field <b>uuid32</b>

<dd>
<p>The union member for a 32-bit UUID.</p>
</dd>

### -field <b>uuid16</b>

<dd>
<p>
      The union member for a 16-bit UUID.
     </p>
</dd>

### -field <b>int64</b>

<dd>
<p>
      The union member for a 64-bit integer.
     </p>
</dd>

### -field <b>uint64</b>

<dd>
<p>The union member for an unsigned 64-bit integer.</p>
</dd>

### -field <b>int32</b>

<dd>
<p>The union member for a 32-bit integer.</p>
</dd>

### -field <b>uint32</b>

<dd>
<p>The union member for an unsigned 32-bit integer.</p>
</dd>

### -field <b>int16</b>

<dd>
<p>The union member for a 16-bit integer.</p>
</dd>

### -field <b>uint16</b>

<dd>
<p>The union member for an unsigned 16-bit integer.</p>
</dd>

### -field <b>int8</b>

<dd>
<p>The union reserved for an 8-bit integer.</p>
</dd>

### -field <b>uint8</b>

<dd>
<p>The union member for an unsigned 8-bit integer.</p>
</dd>

### -field <b>boolean</b>

<dd>
<p>The union member for a Boolean value.</p>
</dd>

### -field <b>string</b>

<dd>
<p>
      The union member for a string value.
     </p>
</dd>

### -field <b>url</b>

<dd>
<p>The union member for a URL value.</p>
</dd>

### -field <b>sequence</b>

<dd>
<p>An 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536850">SDP_NODE_HEADER</a> structure that references
     the elements of a sequence.</p>
</dd>

### -field <b>alternative</b>

<dd>
<p>An SDP_NODE_HEADER structure that references the elements of an alternate list sequence.</p>
</dd>

### -field <b>container</b>

<dd>
<p>A list of pointers to user-mode specific interfaces.</p>
</dd>

### -field ( <i>unnamed struct</i> )

<dd>
<p>The union member for a 128-bit integer.</p>
<dl>

### -field <b>stream</b>

<dd>
<p>
       The address of a portion of the original SDP stream that produced the current SDP node.
      </p>
</dd>

### -field <b>streamLength</b>

<dd>
<p>
       The length of the portion of the original SDP stream that produced the current SDP node.
      </p>
</dd>
</dl>
</dd>
</dl>

## -remarks
<p>Each 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536848">SDP_NODE</a> structure in the tree representation of an
    SDP record contains a SDP_NODE_HEADER structure and an SDP_NODE_DATA union.</p>

<p>The header specifies the type of data. Driver developers can access links to peer 
    <b>SDP_NODE</b> structures by calling the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure of the header. By evaluating 
    <code>Node.hdr.Link.Flink</code>and 
    <code>Node.hdr.Link.Blink</code>, drivers can obtain the addresses of peer
    nodes in the tree. Keep in mind that 
    <b>LIST_ENTRY</b> pointers contain the addresses of other LIST_ENTRY structures, and that the profile
    driver must use the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff542043">CONTAINING_RECORD</a> memory manager macro to
    extract the address of the containing node record.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536850">SDP_NODE_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536848">SDP_NODE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542043">CONTAINING_RECORD</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20SDP_NODE_DATA union%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
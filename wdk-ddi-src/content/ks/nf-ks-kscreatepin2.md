---
UID: NF.ks.KsCreatePin2
title: KsCreatePin2
author: windows-driver-content
description: Passes a connection request to a device, creating a pin instance.
old-location: stream\kscreatepin2.htm
ms.assetid: 43408247-0c34-46bd-a36b-b11540a10c55
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsCreatePin2
req.alt-loc: Ks.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: KsCreatePin2
req.iface: 
---

# KsCreatePin2 function



## -description
<p>Passes a connection request to a device, creating a pin instance.</p>
<p>Supported starting in Windows 8.</p>


## -syntax

````
KSDDKAPI HRESULT WINAPI KsCreatePin2(
  _In_  HANDLE         FilterHandle,
  _In_  PKSPIN_CONNECT Connect,
  _In_  ACCESS_MASK    DesiredAccess,
  _Out_ PHANDLE        ConnectionHandle
);
````


## -parameters
<dl>

### -param <i>FilterHandle</i> [in]

<dd>
<p>Specifies the handle of the filter initiating the create request and where the connection will occur. </p>
</dd>

### -param <i>Connect</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563531">KSPIN_CONNECT</a> structure that contains parameters for the requested connection. This should be followed in memory by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561656">KSDATAFORMAT</a> data structure, describing the data format requested for the connection.</p>
</dd>

### -param <i>DesiredAccess</i> [in]

<dd>
<p>Specifies the access desired to the pin. This is typically <b>GENERIC_READ</b> or <b>GENERIC_WRITE</b>. For data flowing into the pin this value should be set to <b>GENERIC_WRITE</b>, and for data flowing out of the pin this should be set to <b>GENERIC_READ</b> regardless of the communication method.</p>
</dd>

### -param <i>ConnectionHandle</i> [out]

<dd>
<p>Specifies the connection handle passed. The routine fills this in with a handle to the file object of the created connection. This value can then be used to disconnect with the <a href="base.closehandle">CloseHandle</a> function.</p>
</dd>
</dl>

## -returns
<p>Returns <b>NOERROR</b> if successful; otherwise, returns an error code.</p>

## -remarks
<p>This is a new version of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561652">KsCreatePin</a> function and uses the device broker to create the handle to the kernel streaming object. In addition, the Component Object Model (COM) <a href="com.coinitialize">CoInitialize</a> function must be called before this function is called.</p>

<p>The routine sends an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a> request to the driver. The driver accepts the request only if the interface, medium, and data format are compatible.</p>

<p>If <i>Connect</i>-&gt;<b>PinToHandle</b> is <b>NULL</b>, <b>KsCreatePin2</b> creates a pin that the caller can use to send requests to the streaming driver specified in <i>Connect</i>-&gt;<b>FilterHandle</b>. <i>Connect</i>-&gt;<b>PinId</b> determines the type of pin to be created.</p>

<p>This is a new version of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561652">KsCreatePin</a> function and uses the device broker to create the handle to the kernel streaming object. In addition, the Component Object Model (COM) <a href="com.coinitialize">CoInitialize</a> function must be called before this function is called.</p>

<p>The routine sends an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a> request to the driver. The driver accepts the request only if the interface, medium, and data format are compatible.</p>

<p>If <i>Connect</i>-&gt;<b>PinToHandle</b> is <b>NULL</b>, <b>KsCreatePin2</b> creates a pin that the caller can use to send requests to the streaming driver specified in <i>Connect</i>-&gt;<b>FilterHandle</b>. <i>Connect</i>-&gt;<b>PinId</b> determines the type of pin to be created.</p>

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
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="com.coinitialize">CoInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561652">KsCreatePin</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561656">KSDATAFORMAT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563531">KSPIN_CONNECT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsCreatePin2 function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
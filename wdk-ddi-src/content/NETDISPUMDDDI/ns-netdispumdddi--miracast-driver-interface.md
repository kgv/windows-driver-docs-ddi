---
UID: NS.netdispumdddi._MIRACAST_DRIVER_INTERFACE
title: MIRACAST_DRIVER_INTERFACE
author: windows-driver-content
description: Contains pointers to wireless display (Miracast) functions that are implemented by the Miracast user-mode driver.
old-location: display\miracast_driver_interface.htm
ms.assetid: a3b9695e-b317-471b-91de-e191c1f5cb17
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: netdispumdddi.h
req.include-header: Netdispumdddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MIRACAST_DRIVER_INTERFACE
req.alt-loc: Netdispumdddi.h
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
ms.keywords: MIRACAST_DRIVER_INTERFACE, MIRACAST_DRIVER_INTERFACE, *PMIRACAST_DRIVER_INTERFACE
req.iface: 
---

# MIRACAST_DRIVER_INTERFACE structure



## -description
<p>Contains pointers to wireless display (Miracast) functions that are implemented by the Miracast user-mode driver.</p>


## -syntax

````
typedef struct _MIRACAST_DRIVER_INTERFACE {
  UINT                         Size;
  PFN_CREATE_MIRACAST_CONTEXT  CreateMiracastContext;
  PFN_DESTROY_MIRACAST_CONTEXT DestroyMiracastContext;
  PFN_START_MIRACAST_SESSION   StartMiracastSession;
  PFN_STOP_MIRACAST_SESSION    StopMiracastSession;
  PFN_HANDLE_KMD_MESSAGE       HandleKernelModeMessage;
} MIRACAST_DRIVER_INTERFACE, *PMIRACAST_DRIVER_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>The size, in bytes, of the <b>MIRACAST_DRIVER_INTERFACE</b> structure that the driver returns when the operating system calls the <a href="https://msdn.microsoft.com/a8833f8c-7e3f-422c-922e-e75476358ee9">QueryMiracastDriverInterface</a> function.</p>
</dd>

### -field <b>CreateMiracastContext</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/3b10ddd9-a48d-4f96-b35e-db017d1f9583">CreateMiracastContext</a> function.</p>
</dd>

### -field <b>DestroyMiracastContext</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/1b155e15-1e4e-45bb-98cc-f1c19923ed2c">DestroyMiracastContext</a> function.</p>
</dd>

### -field <b>StartMiracastSession</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/2778d9d0-7f97-416f-a5ae-3754b17e8a29">StartMiracastSession</a> function.</p>
</dd>

### -field <b>StopMiracastSession</b>

<dd>
<p>A pointer to the driver's   <a href="https://msdn.microsoft.com/ab9ad8ee-9390-41a4-9a69-2e98579b2b77">StopMiracastSession</a> function.</p>
</dd>

### -field <b>HandleKernelModeMessage</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/9DE4F3B0-915A-4C66-85F8-AE248B8471B5">HandleKernelModeMessage</a> function.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012 R2</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Netdispumdddi.h (include Netdispumdddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/3b10ddd9-a48d-4f96-b35e-db017d1f9583">CreateMiracastContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1b155e15-1e4e-45bb-98cc-f1c19923ed2c">DestroyMiracastContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/9DE4F3B0-915A-4C66-85F8-AE248B8471B5">HandleKernelModeMessage</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a8833f8c-7e3f-422c-922e-e75476358ee9">QueryMiracastDriverInterface</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2778d9d0-7f97-416f-a5ae-3754b17e8a29">StartMiracastSession</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ab9ad8ee-9390-41a4-9a69-2e98579b2b77">StopMiracastSession</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20MIRACAST_DRIVER_INTERFACE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
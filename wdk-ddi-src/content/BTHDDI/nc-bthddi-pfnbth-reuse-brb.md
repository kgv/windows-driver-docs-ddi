---
UID: NC.bthddi.PFNBTH_REUSE_BRB
title: PFNBTH_REUSE_BRB
author: windows-driver-content
description: The BthReuseBrb function reinitializes a Bluetooth request block (BRB) to be reused.
old-location: bltooth\bthreusebrb.htm
ms.assetid: cdf156a1-1556-441a-ae3d-9a49daf47990
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthddi.h
req.include-header: Bthddi.h
req.target-type: Desktop
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BthReuseBrb
req.alt-loc: bthddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: IBidiSpl2, UnbindDevice, IBidiSpl2::UnbindDevice
req.iface: IBidiSpl2
---

# PFNBTH_REUSE_BRB callback



## -description
<p>The 
  <i>BthReuseBrb</i> function reinitializes a Bluetooth request block (BRB) to be reused.</p>


## -prototype

````
PFNBTH_REUSE_BRB BthReuseBrb;

VOID BthReuseBrb(
  _Inout_ PBRB     pBrb,
  _In_    BRB_TYPE brbType
)
{ ... }
````


## -parameters
<dl>

### -param <i>pBrb</i> [in, out]

<dd>
<p>Pointer to the BRB to reuse.</p>
</dd>

### -param <i>brbType</i> [in]

<dd>
<p>Specifies a value from the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536631">BRB_TYPE</a> enumeration to initialize the BRB
     with.</p>
</dd>
</dl>

## -returns
<p>None.</p>

## -remarks
<p>Profile drivers obtain a pointer to the 
    <i>BthReuseBrb</i> function when they query the Bluetooth driver stack for an instance of the
    BTHDDI_PROFILE_DRIVER_INTERFACE driver interface. See 
    <a href="https://msdn.microsoft.com/56db29cd-26ab-4262-9b9f-40d46372ffe9">Querying for Bluetooth
    Interfaces</a> for more information about querying the Bluetooth driver stack.</p>

<p>Profile drivers obtain a pointer to the 
    <i>BthReuseBrb</i> function when they query the Bluetooth driver stack for an instance of the
    BTHDDI_PROFILE_DRIVER_INTERFACE driver interface. See 
    <a href="https://msdn.microsoft.com/56db29cd-26ab-4262-9b9f-40d46372ffe9">Querying for Bluetooth
    Interfaces</a> for more information about querying the Bluetooth driver stack.</p>

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
<dt>Bthddi.h (include Bthddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536631">BRB_TYPE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20PFNBTH_REUSE_BRB callback function%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
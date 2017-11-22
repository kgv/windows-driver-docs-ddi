---
UID: NS.winddiui._DRIVER_UPGRADE_INFO_1
title: DRIVER_UPGRADE_INFO_1
author: windows-driver-content
description: The DRIVER_UPGRADE_INFO_1 structure is used as an input to a printer interface DLL's DrvUpgradePrinter function.
old-location: print\driver_upgrade_info_1.htm
ms.assetid: fef7c63b-ca9e-47f4-96cb-4dafa080ddcf
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: winddiui.h
req.include-header: Winddiui.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DRIVER_UPGRADE_INFO_1
req.alt-loc: winddiui.h
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
ms.keywords: DRIVER_UPGRADE_INFO_1, DRIVER_UPGRADE_INFO_1, *PDRIVER_UPGRADE_INFO_1
req.iface: 
req.product: Windows 10 or later.
---

# DRIVER_UPGRADE_INFO_1 structure



## -description
<p>The DRIVER_UPGRADE_INFO_1 structure is used as an input to a printer interface DLL's <a href="https://msdn.microsoft.com/library/windows/hardware/ff548648">DrvUpgradePrinter</a> function.</p>


## -syntax

````
typedef struct _DRIVER_UPGRADE_INFO_1 {
  LPTSTR pPrinterName;
  LPTSTR pOldDriverDirectory;
} DRIVER_UPGRADE_INFO_1, *PDRIVER_UPGRADE_INFO_1;
````


## -struct-fields
<dl>

### -field <b>pPrinterName</b>

<dd>
<p>Pointer to a NULL-terminated string that specifies the name of the printer.</p>
</dd>

### -field <b>pOldDriverDirectory</b>

<dd>
<p>Pointer to a NULL-terminated string that specifies the local directory in which the old printer driver files can be found.</p>
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
<dt>Winddiui.h (include Winddiui.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548648">DrvUpgradePrinter</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548527">DRIVER_UPGRADE_INFO_2</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20DRIVER_UPGRADE_INFO_1 structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
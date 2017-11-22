---
UID: NE.d3dkmdt._DXGKMDT_OPM_STATUS
title: DXGKMDT_OPM_STATUS
author: windows-driver-content
description: The DXGKMDT_OPM_STATUS enumeration identifies the status of a protected output.
old-location: display\dxgkmdt_opm_status.htm
ms.assetid: e3bfde85-e8a0-41df-9248-f48ceb8b5304
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmdt.h
req.include-header: D3dkmdt.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGKMDT_OPM_STATUS
req.alt-loc: d3dkmdt.h
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
ms.keywords: DXGK_CHECK_MULTIPLANE_OVERLAY_SUPPORT_RETURN_INFO, DXGK_CHECK_MULTIPLANE_OVERLAY_SUPPORT_RETURN_INFO
req.iface: 
---

# DXGKMDT_OPM_STATUS enumeration



## -description
<p>The DXGKMDT_OPM_STATUS enumeration identifies the status of a protected output. </p>


## -syntax

````
typedef enum _DXGKMDT_OPM_STATUS { 
  DXGKMDT_OPM_STATUS_NORMAL                        = 0x00,
  DXGKMDT_OPM_STATUS_LINK_LOST                     = 0x01,
  DXGKMDT_OPM_STATUS_RENEGOTIATION_REQUIRED        = 0x02,
  DXGKMDT_OPM_STATUS_TAMPERING_DETECTED            = 0x04,
  DXGKMDT_OPM_STATUS_REVOKED_HDCP_DEVICE_ATTACHED  = 0x08
} DXGKMDT_OPM_STATUS;
````


## -enum-fields
<dl>

### -field <a id="DXGKMDT_OPM_STATUS_NORMAL"></a><a id="dxgkmdt_opm_status_normal"></a><b>DXGKMDT_OPM_STATUS_NORMAL</b>

<dd>
<p>Indicates that the protected output is working correctly. </p>
</dd>

### -field <a id="DXGKMDT_OPM_STATUS_LINK_LOST"></a><a id="dxgkmdt_opm_status_link_lost"></a><b>DXGKMDT_OPM_STATUS_LINK_LOST</b>

<dd>
<p>Indicates that although the protected output detected no tampering, an output protection technology unexpectedly stopped working. </p>
<p>This status bit must be set if DXGKMDT_OPM_STATUS_REVOKED_HDCP_DEVICE_ATTACHED is also set. </p>
</dd>

### -field <a id="DXGKMDT_OPM_STATUS_RENEGOTIATION_REQUIRED"></a><a id="dxgkmdt_opm_status_renegotiation_required"></a><b>DXGKMDT_OPM_STATUS_RENEGOTIATION_REQUIRED</b>

<dd>
<p>Indicates that the end user caused the configuration of the physical connector to change. Therefore, a renegotiation is required. </p>
</dd>

### -field <a id="DXGKMDT_OPM_STATUS_TAMPERING_DETECTED"></a><a id="dxgkmdt_opm_status_tampering_detected"></a><b>DXGKMDT_OPM_STATUS_TAMPERING_DETECTED</b>

<dd>
<p>Indicates that tampering with the graphics adapter or the adapter's display miniport driver has occurred. </p>
</dd>

### -field <a id="DXGKMDT_OPM_STATUS_REVOKED_HDCP_DEVICE_ATTACHED"></a><a id="dxgkmdt_opm_status_revoked_hdcp_device_attached"></a><b>DXGKMDT_OPM_STATUS_REVOKED_HDCP_DEVICE_ATTACHED</b>

<dd>
<p>Indicates that a revoked High-bandwidth Digital Content Protection (HDCP) device is directly or indirectly attached to a protected output. If HDCP is not enabled, the protected output is not required to detect revoked devices. If HDCP is enabled, the protected output must detect revoked devices. The driver sets this status value only from a call to its <a href="https://msdn.microsoft.com/3d6559e5-776e-4fc0-b99a-8818cbcc289d">DxgkDdiOPMGetInformation</a> function to determine if HDCP is enabled. </p>
</dd>
</dl>

## -remarks
<p>The display miniport driver returns status about a protected output whenever the driver's <a href="https://msdn.microsoft.com/3d6559e5-776e-4fc0-b99a-8818cbcc289d">DxgkDdiOPMGetInformation</a> and <a href="https://msdn.microsoft.com/9f15df1e-bdf5-4634-97f1-78515664b594">DxgkDdiOPMGetCOPPCompatibleInformation</a> functions are called to retrieve information about the protected output. For more information about returning a protected output's status, see <a href="https://msdn.microsoft.com/9945ae9c-1c11-4266-8a5c-d0ffe5ba4b5f">Reporting Status about a Protected Output</a>.</p>

<p>The display miniport driver returns status about a protected output whenever the driver's <a href="https://msdn.microsoft.com/3d6559e5-776e-4fc0-b99a-8818cbcc289d">DxgkDdiOPMGetInformation</a> and <a href="https://msdn.microsoft.com/9f15df1e-bdf5-4634-97f1-78515664b594">DxgkDdiOPMGetCOPPCompatibleInformation</a> functions are called to retrieve information about the protected output. For more information about returning a protected output's status, see <a href="https://msdn.microsoft.com/9945ae9c-1c11-4266-8a5c-d0ffe5ba4b5f">Reporting Status about a Protected Output</a>.</p>

<p>The display miniport driver returns status about a protected output whenever the driver's <a href="https://msdn.microsoft.com/3d6559e5-776e-4fc0-b99a-8818cbcc289d">DxgkDdiOPMGetInformation</a> and <a href="https://msdn.microsoft.com/9f15df1e-bdf5-4634-97f1-78515664b594">DxgkDdiOPMGetCOPPCompatibleInformation</a> functions are called to retrieve information about the protected output. For more information about returning a protected output's status, see <a href="https://msdn.microsoft.com/9945ae9c-1c11-4266-8a5c-d0ffe5ba4b5f">Reporting Status about a Protected Output</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmdt.h (include D3dkmdt.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/9f15df1e-bdf5-4634-97f1-78515664b594">DxgkDdiOPMGetCOPPCompatibleInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3d6559e5-776e-4fc0-b99a-8818cbcc289d">DxgkDdiOPMGetInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560830">DXGKMDT_OPM_ACP_AND_CGMSA_SIGNALING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560840">DXGKMDT_OPM_ACTUAL_OUTPUT_FORMAT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560854">DXGKMDT_OPM_CONNECTED_HDCP_DEVICE_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560925">DXGKMDT_OPM_STANDARD_INFORMATION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKMDT_OPM_STATUS enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
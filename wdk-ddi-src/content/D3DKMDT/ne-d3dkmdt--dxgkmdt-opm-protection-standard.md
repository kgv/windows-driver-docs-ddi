---
UID: NE.d3dkmdt._DXGKMDT_OPM_PROTECTION_STANDARD
title: DXGKMDT_OPM_PROTECTION_STANDARD
author: windows-driver-content
description: The DXGKMDT_OPM_PROTECTION_STANDARD enumeration indicates the type of television signal for which a video output supports protection.
old-location: display\dxgkmdt_opm_protection_standard.htm
ms.assetid: 9f079edf-312a-4218-8b73-0325ccca5a05
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
req.alt-api: DXGKMDT_OPM_PROTECTION_STANDARD
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

# DXGKMDT_OPM_PROTECTION_STANDARD enumeration



## -description
<p>The DXGKMDT_OPM_PROTECTION_STANDARD enumeration indicates the type of television signal for which a video output supports protection.</p>


## -syntax

````
typedef enum _DXGKMDT_OPM_PROTECTION_STANDARD { 
  DXGKMDT_OPM_PROTECTION_STANDARD_OTHER                = 0x80000000,
  DXGKMDT_OPM_PROTECTION_STANDARD_NONE                 = 0x00000000,
  DXGKMDT_OPM_PROTECTION_STANDARD_IEC61880_525I        = 0x00000001,
  DXGKMDT_OPM_PROTECTION_STANDARD_IEC61880_2_525I      = 0x00000002,
  DXGKMDT_OPM_PROTECTION_STANDARD_IEC62375_625P        = 0x00000004,
  DXGKMDT_OPM_PROTECTION_STANDARD_EIA608B_525          = 0x00000008,
  DXGKMDT_OPM_PROTECTION_STANDARD_EN300294_625I        = 0x00000010,
  DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_525P   = 0x00000020,
  DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_750P   = 0x00000040,
  DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_1125I  = 0x00000080,
  DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_525P   = 0x00000100,
  DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_750P   = 0x00000200,
  DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_1125I  = 0x00000400,
  DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_525I       = 0x00000800,
  DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_525P       = 0x00001000,
  DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_750P       = 0x00002000,
  DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_1125I      = 0x00004000
} DXGKMDT_OPM_PROTECTION_STANDARD;
````


## -enum-fields
<dl>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_OTHER"></a><a id="dxgkmdt_opm_protection_standard_other"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_OTHER</b>

<dd>
<p>Indicates a protected television signal type other than those given in the following constants of this enumeration. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_NONE"></a><a id="dxgkmdt_opm_protection_standard_none"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_NONE</b>

<dd>
<p>Indicates that the video output does not support protection for any television signals. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_IEC61880_525I"></a><a id="dxgkmdt_opm_protection_standard_iec61880_525i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_IEC61880_525I</b>

<dd>
<p>Indicates that the video output supports the IEC61880_525I standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_IEC61880_2_525I"></a><a id="dxgkmdt_opm_protection_standard_iec61880_2_525i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_IEC61880_2_525I</b>

<dd>
<p>Indicates that the video output supports the IEC61880_2_525I standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_IEC62375_625P"></a><a id="dxgkmdt_opm_protection_standard_iec62375_625p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_IEC62375_625P</b>

<dd>
<p>Indicates that the video output supports the IEC62375_625P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_EIA608B_525"></a><a id="dxgkmdt_opm_protection_standard_eia608b_525"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_EIA608B_525</b>

<dd>
<p>Indicates that the video output supports the EIA608B_525 standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_EN300294_625I"></a><a id="dxgkmdt_opm_protection_standard_en300294_625i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_EN300294_625I</b>

<dd>
<p>Indicates that the video output supports the EN300294_625I standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_525P"></a><a id="dxgkmdt_opm_protection_standard_cea805a_typea_525p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_525P</b>

<dd>
<p>Indicates that the video output supports the CEA805A_TYPEA_525P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_750P"></a><a id="dxgkmdt_opm_protection_standard_cea805a_typea_750p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_750P</b>

<dd>
<p>Indicates that the video output supports the CEA805A_TYPEA_750P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_1125I"></a><a id="dxgkmdt_opm_protection_standard_cea805a_typea_1125i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEA_1125I</b>

<dd>
<p>Indicates that the video output supports the CEA805A_TYPEA_1125I standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_525P"></a><a id="dxgkmdt_opm_protection_standard_cea805a_typeb_525p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_525P</b>

<dd>
<p>Indicates that the video output supports the CEA805A_TYPEB_525P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_750P"></a><a id="dxgkmdt_opm_protection_standard_cea805a_typeb_750p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_750P</b>

<dd>
<p>Indicates that the video output supports the CEA805A_TYPEB_750P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_1125I"></a><a id="dxgkmdt_opm_protection_standard_cea805a_typeb_1125i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_CEA805A_TYPEB_1125I</b>

<dd>
<p>Indicates that the video output supports the CEA805A_TYPEB_1125I standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_525I"></a><a id="dxgkmdt_opm_protection_standard_aribtrb15_525i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_525I</b>

<dd>
<p>Indicates that the video output supports the ARIBTRB15_525I standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_525P"></a><a id="dxgkmdt_opm_protection_standard_aribtrb15_525p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_525P</b>

<dd>
<p>Indicates that the video output supports the ARIBTRB15_525P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_750P"></a><a id="dxgkmdt_opm_protection_standard_aribtrb15_750p"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_750P</b>

<dd>
<p>Indicates that the video output supports the ARIBTRB15_750P standard. </p>
</dd>

### -field <a id="DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_1125I"></a><a id="dxgkmdt_opm_protection_standard_aribtrb15_1125i"></a><b>DXGKMDT_OPM_PROTECTION_STANDARD_ARIBTRB15_1125I</b>

<dd>
<p>Indicates that the video output supports the ARIBTRB15_1125I standard. </p>
</dd>
</dl>

## -remarks


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
<a href="https://msdn.microsoft.com/a7829587-c1e7-43ec-a0bb-92bca94b7c3d">DxgkDdiOPMConfigureProtectedOutput</a>
</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560913">DXGKMDT_OPM_SET_ACP_AND_CGMSA_SIGNALING_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKMDT_OPM_PROTECTION_STANDARD enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
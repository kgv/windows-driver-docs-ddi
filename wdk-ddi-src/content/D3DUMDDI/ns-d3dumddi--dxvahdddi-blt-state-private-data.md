---
UID: NS.d3dumddi._DXVAHDDDI_BLT_STATE_PRIVATE_DATA
title: DXVAHDDDI_BLT_STATE_PRIVATE_DATA
author: windows-driver-content
description: The DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure describes data that specifies the private bit-block transfer (bitblt) state.
old-location: display\dxvahdddi_blt_state_private_data.htm
ms.assetid: f9c0f137-e84c-4626-aa6a-dce352bf7bb0
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: DXVAHDDDI_BLT_STATE_PRIVATE_DATA is supported beginning with the Windows 7 operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXVAHDDDI_BLT_STATE_PRIVATE_DATA
req.alt-loc: d3dumddi.h
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
ms.keywords: DXVAHDDDI_BLT_STATE_PRIVATE_DATA, DXVAHDDDI_BLT_STATE_PRIVATE_DATA
req.iface: 
---

# DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure



## -description
<p>The DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure describes data that specifies the private bit-block transfer (bitblt) state. </p>


## -syntax

````
typedef struct _DXVAHDDDI_BLT_STATE_PRIVATE_DATA {
  GUID Guid;
  UINT DataSize;
  VOID *pData;
} DXVAHDDDI_BLT_STATE_PRIVATE_DATA;
````


## -struct-fields
<dl>

### -field <b>Guid</b>

<dd>
<p>[in] A GUID that identifies the private bitblt state.  </p>
</dd>

### -field <b>DataSize</b>

<dd>
<p>[in] The size, in bytes, of the private bitblt state data. </p>
</dd>

### -field <b>pData</b>

<dd>
<p>[in/out] A pointer to the private bitblt state data. The caller sets <b>pData</b> to <b>NULL</b> to retrieve the size of the private bitblt state data. </p>
</dd>
</dl>

## -remarks
<p>Unlike other bitblt states (<a href="https://msdn.microsoft.com/library/windows/hardware/ff562978">DXVAHDDDI_BLT_STATE</a>), the Direct3D runtime does not maintain the private bitblt state. An application and the driver communicate the private bitblt state directly in a proprietary manner, which consists of setting and retrieving the private bitblt state. To set private bitblt state, the application causes the Direct3D runtime to specify the DXVAHDDDI_BLT_STATE_PRIVATE state in the <b>State</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543093">D3DDDIARG_DXVAHD_SETVIDEOPROCESSBLTSTATE</a> structure in a call to the driver's <a href="https://msdn.microsoft.com/6796372c-279d-427c-a2a4-9b7c99494f53">SetVideoProcessBltState</a> function. To retrieve private bitblt state, the application causes the Direct3D runtime to call the driver's <a href="https://msdn.microsoft.com/bb4c04cf-0125-47bf-8fc8-88d807e7b6ad">GetVideoProcessBltStatePrivate</a> function. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>DXVAHDDDI_BLT_STATE_PRIVATE_DATA is supported beginning with the Windows 7 operating system.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543093">D3DDDIARG_DXVAHD_SETVIDEOPROCESSBLTSTATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562978">DXVAHDDDI_BLT_STATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/bb4c04cf-0125-47bf-8fc8-88d807e7b6ad">GetVideoProcessBltStatePrivate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/6796372c-279d-427c-a2a4-9b7c99494f53">SetVideoProcessBltState</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVAHDDDI_BLT_STATE_PRIVATE_DATA structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
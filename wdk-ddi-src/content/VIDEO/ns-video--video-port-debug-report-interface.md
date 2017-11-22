---
UID: NS.video._VIDEO_PORT_DEBUG_REPORT_INTERFACE
title: VIDEO_PORT_DEBUG_REPORT_INTERFACE
author: windows-driver-content
description: The VIDEO_PORT_DEBUG_REPORT_INTERFACE structure holds pointers to the Debug Report functions, which are implemented by the video port driver.
old-location: display\video_port_debug_report_interface.htm
ms.assetid: 11536f1e-523c-4796-a973-e53291c756a8
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: VIDEO_PORT_DEBUG_REPORT_INTERFACE
req.alt-loc: video.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section.
ms.keywords: VIDEO_PORT_DEBUG_REPORT_INTERFACE, VIDEO_PORT_DEBUG_REPORT_INTERFACE, *PVIDEO_PORT_DEBUG_REPORT_INTERFACE
req.iface: 
req.product: Windows 10 or later.
---

# VIDEO_PORT_DEBUG_REPORT_INTERFACE structure



## -description
<p>The VIDEO_PORT_DEBUG_REPORT_INTERFACE structure holds pointers to the Debug Report functions, which are implemented by the video port driver.</p>


## -syntax

````
typedef struct _VIDEO_PORT_DEBUG_REPORT_INTERFACE {
  USHORT                 Size;
  USHORT                 Version;
  PVOID                  Context;
  PINTERFACE_REFERENCE   InterfaceReference;
  PINTERFACE_DEREFERENCE InterfaceDereference;
  PVIDEO_DEBUG_REPORT    (*DbgReportCreate)(
      _In_ PVOID HwDeviceExtension, 
      _In_ ULONG ulCode, 
      _In_ ULONG_PTR ulpArg1, 
      _In_ ULONG_PTR ulpArg2, 
      _In_ ULONG_PTR ulpArg3, 
      _In_ ULONG_PTR ulpArg4);
  BOOLEAN                (*DbgReportSecondaryData)(
      _In_ PVIDEO_DEBUG_REPORT pReport, 
      _In_ PVOID pvData, 
      _In_ ULONG ulDataSize);
  VOID                   (*DbgReportComplete)(_Inout_opt_ PVIDEO_DEBUG_REPORT pReport);
} VIDEO_PORT_DEBUG_REPORT_INTERFACE, *PVIDEO_PORT_DEBUG_REPORT_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Specifies the size, in bytes, of this structure.</p>
</dd>

### -field <b>Version</b>

<dd>
<p>Specifies the version of the interface returned by the video port driver. Currently, the only supported version is VIDEO_PORT_DEBUG_REPORT_INTERFACE_VERSION_1.</p>
</dd>

### -field <b>Context</b>

<dd>
<p>Pointer to a context that is provided by the video port driver.</p>
</dd>

### -field <b>InterfaceReference</b>

<dd>
<p>Pointer to an interface reference function that is implemented by the video port driver.</p>
</dd>

### -field <b>InterfaceDereference</b>

<dd>
<p>Pointer to an interface dereference function that is implemented by the video port driver.</p>
</dd>

### -field <b>DbgReportCreate</b>

<dd>
<p>Pointer to the video port driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff549088">DbgReportCreate</a> function. </p>
</dd>

### -field <b>DbgReportSecondaryData</b>

<dd>
<p>Pointer to the video port driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff549099">DbgReportSecondaryData</a> function. </p>
</dd>

### -field <b>DbgReportComplete</b>

<dd>
<p>Pointer to the video port driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff549080">DbgReportComplete</a> function. </p>
</dd>
</dl>

## -remarks
<p>This structure is available in the following operating systems:</p>

<p>Windows Server 2003 SP1 and subsequent service packs</p>

<p>Windows XP SP2 and subsequent service packs</p>

<p>The video miniport driver supplies the <b>Size</b> and <b>Version</b> members of this structure, and then calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff570337">VideoPortQueryServices</a>, which initializes the remaining members of this structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549088">DbgReportCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549099">DbgReportSecondaryData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549080">DbgReportComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570337">VideoPortQueryServices</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20VIDEO_PORT_DEBUG_REPORT_INTERFACE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NS.wudfworkitem._WUDF_WORKITEM_CONFIG
title: WUDF_WORKITEM_CONFIG
author: windows-driver-content
description: The WUDF_WORKITEM_CONFIG structure contains information that is associated with a work item.
old-location: wdf\wudf_workitem_config.htm
ms.assetid: 877C6641-30F9-44BC-9286-3B1D880482C9
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfworkitem.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.11
req.alt-api: WUDF_WORKITEM_CONFIG
req.alt-loc: wudfworkitem.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: WUDF_WORKITEM_CONFIG, WUDF_WORKITEM_CONFIG, *PWUDF_WORKITEM_CONFIG
req.iface: 
req.product: Windows 10 or later.
---

# WUDF_WORKITEM_CONFIG structure



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The 
   
  <b>WUDF_WORKITEM_CONFIG</b> structure contains information that is associated with a work item.</p>


## -syntax

````
typedef struct _WUDF_WORKITEM_CONFIG {
  ULONG             Size;
  PFN_WUDF_WORKITEM OnWorkItemFunc;
  BOOLEAN           AutomaticSerialization;
} WUDF_WORKITEM_CONFIG, *PWUDF_WORKITEM_CONFIG;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>The size, in bytes, of this structure.</p>
</dd>

### -field <b>OnWorkItemFunc</b>

<dd>
<p>The address of an <a href="https://msdn.microsoft.com/4CCA1F5E-C92E-4D8D-A8C0-B8E9A0F29703">OnWorkItem</a> callback function.</p>
</dd>

### -field <b>AutomaticSerialization</b>

<dd>
<p>A Boolean value that, if TRUE, indicates that the framework will synchronize execution of the <a href="https://msdn.microsoft.com/4CCA1F5E-C92E-4D8D-A8C0-B8E9A0F29703">OnWorkItem</a> callback function with callback functions from other objects that are underneath the work-item object's parent object. If FALSE, the framework does not synchronize execution of the <i>OnWorkItem</i> callback function.

</p>
</dd>
</dl>

## -remarks
<p>Your driver must initialize the <b>WUDF_WORKITEM_CONFIG</b> structure by calling <a href="https://msdn.microsoft.com/library/windows/hardware/hh464097">WUDF_WORKITEM_CONFIG_INIT</a>. Your driver can then pass the structure to the <a href="https://msdn.microsoft.com/B34EABF4-C659-4DB4-AEC6-94F544D79221">IWDFDevice3::CreateWorkItem</a> method as an input parameter.</p>

<p>Setting the <b>AutomaticSerialization</b> member of <b>WUDF_WORKITEM_CONFIG</b> to TRUE has no effect if the driver did not enable automatic callback synchronization by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff556991">IWDFDeviceInitialize::SetLockingConstraint</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>End of support</p>
</th>
<td width="70%">
<p>Unavailable in UMDF 2.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.11</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfworkitem.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/4CCA1F5E-C92E-4D8D-A8C0-B8E9A0F29703">OnWorkItem</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh464097">WUDF_WORKITEM_CONFIG_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/B34EABF4-C659-4DB4-AEC6-94F544D79221">IWDFDevice3::CreateWorkItem</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WUDF_WORKITEM_CONFIG structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
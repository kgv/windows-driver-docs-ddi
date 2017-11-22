---
UID: NF.wudfddi.IWDFCmResourceList.GetCount
title: IWDFCmResourceList::GetCount
author: windows-driver-content
description: The GetCount method returns the number of resource descriptors that are contained in this interface's resource list.
old-location: wdf\iwdfcmresourcelist_getcount.htm
ms.assetid: 91F88EC2-C0BD-42E1-8C57-437909E2CCA2
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.11
req.alt-api: IWDFCmResourceList.GetCount
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: <= DISPATCH_LEVEL
ms.keywords: IWDFCmResourceList, GetCount, IWDFCmResourceList::GetCount
req.iface: IWDFCmResourceList
req.product: Windows 10 or later.
---

# IWDFCmResourceList::GetCount method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>
<p>The <b>GetCount</b> method returns the number of resource descriptors that are contained in this interface's resource list.</p>
</p>
<p>The <b>GetCount</b> method returns the number of resource descriptors that are contained in this interface's resource list.</p>


## -syntax

````
ULONG GetCount();
````


## -parameters


## -returns
<p><b>GetCount</b> returns the number of resource descriptors that are contained in this interface's resource list.</p>

<p><b>GetCount</b> returns the number of resource descriptors that are contained in this interface's resource list.</p>

<p><b>GetCount</b> returns the number of resource descriptors that are contained in this interface's resource list.</p>

## -remarks
<p>Typically, a UMDF driver calls the <b>GetCount</b> method from its <a href="https://msdn.microsoft.com/library/windows/hardware/hh439734">OnPrepareHardware</a> method. For more information about parsing hardware resources, see <a href="wdf.finding_and_mapping_hardware_resources_in_a_umdf_driver">Finding and Mapping Hardware Resources in a UMDF Driver</a>.</p>

<p>See example code in <a href="https://msdn.microsoft.com/243C7299-7C74-408A-8FB9-32FB3315251F">IWDFDevice3::MapIoSpace</a>.</p>

<p>Typically, a UMDF driver calls the <b>GetCount</b> method from its <a href="https://msdn.microsoft.com/library/windows/hardware/hh439734">OnPrepareHardware</a> method. For more information about parsing hardware resources, see <a href="wdf.finding_and_mapping_hardware_resources_in_a_umdf_driver">Finding and Mapping Hardware Resources in a UMDF Driver</a>.</p>

<p>See example code in <a href="https://msdn.microsoft.com/243C7299-7C74-408A-8FB9-32FB3315251F">IWDFDevice3::MapIoSpace</a>.</p>

<p>Typically, a UMDF driver calls the <b>GetCount</b> method from its <a href="https://msdn.microsoft.com/library/windows/hardware/hh439734">OnPrepareHardware</a> method. For more information about parsing hardware resources, see <a href="wdf.finding_and_mapping_hardware_resources_in_a_umdf_driver">Finding and Mapping Hardware Resources in a UMDF Driver</a>.</p>

<p>See example code in <a href="https://msdn.microsoft.com/243C7299-7C74-408A-8FB9-32FB3315251F">IWDFDevice3::MapIoSpace</a>.</p>

<p>Typically, a UMDF driver calls the <b>GetCount</b> method from its <a href="https://msdn.microsoft.com/library/windows/hardware/hh439734">OnPrepareHardware</a> method. For more information about parsing hardware resources, see <a href="wdf.finding_and_mapping_hardware_resources_in_a_umdf_driver">Finding and Mapping Hardware Resources in a UMDF Driver</a>.</p>

<p>See example code in <a href="https://msdn.microsoft.com/243C7299-7C74-408A-8FB9-32FB3315251F">IWDFDevice3::MapIoSpace</a>.</p>

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
<dt>Wudfddi.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439762">IWDFCmResourceList</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFCmResourceList::GetCount method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
---
UID: NF.dbgeng.IDebugClient5.AddDumpInformationFile
title: IDebugClient5::AddDumpInformationFile
author: windows-driver-content
description: The AddDumpInformationFile method registers additional files containing supporting information that will be used when opening a dump file. The Unicode version of this method is AddDumpInformationFileWide.
old-location: debugger\adddumpinformationfile.htm
ms.assetid: c111eb7e-7c42-4848-89d3-177f240fff7f
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugClient2.AddDumpInformationFile,IDebugClient3.AddDumpInformationFile,IDebugClient4.AddDumpInformationFile,IDebugClient5.AddDumpInformationFile
req.alt-loc: dbgeng.h
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
ms.keywords: IDebugClient5, AddDumpInformationFile, IDebugClient5::AddDumpInformationFile
req.iface: IDebugClient5
---

# IDebugClient5::AddDumpInformationFile method



## -description
<p>The <b>AddDumpInformationFile</b> method registers additional files containing supporting information that will be used when opening a dump file.  The Unicode version of this method is <a href="https://msdn.microsoft.com/library/windows/hardware/ff537874">AddDumpInformationFileWide</a>.</p>


## -syntax

````
HRESULT AddDumpInformationFile(
  [in] PCSTR InfoFile,
  [in] ULONG Type
);
````


## -parameters
<dl>

### -param <i>InfoFile</i> [in]

<dd>
<p>Specifies the name of the file containing the supporting information.</p>
</dd>

### -param <i>Type</i> [in]

<dd>
<p>Specifies the type of the file <i>InfoFile</i>.  Currently, only files containing paging file information are supported, and <i>Type</i> must be set to DEBUG_DUMP_FILE_PAGE_FILE_DUMP.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

## -remarks
<p>If supporting information is to be used when opening a dump file, this method or <a href="https://msdn.microsoft.com/library/windows/hardware/ff537874">AddDumpInformationFileWide</a> must be called before <a href="https://msdn.microsoft.com/library/windows/hardware/ff552322">OpenDumpFile</a> is called. If a session has already started, this method cannot be used.</p>

<p>For more information about crash dump files, see <a href="https://msdn.microsoft.com/83fb6753-a6c1-4899-9b06-a6331b3c31a8">Dump File Targets</a>.</p>

<p>If supporting information is to be used when opening a dump file, this method or <a href="https://msdn.microsoft.com/library/windows/hardware/ff537874">AddDumpInformationFileWide</a> must be called before <a href="https://msdn.microsoft.com/library/windows/hardware/ff552322">OpenDumpFile</a> is called. If a session has already started, this method cannot be used.</p>

<p>For more information about crash dump files, see <a href="https://msdn.microsoft.com/83fb6753-a6c1-4899-9b06-a6331b3c31a8">Dump File Targets</a>.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550481">IDebugClient2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550488">IDebugClient3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550494">IDebugClient4</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550497">IDebugClient5</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537874">AddDumpInformationFileWide</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547887">GetNumberDumpFiles</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546586">GetDumpFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552322">OpenDumpFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552324">OpenDumpFileWide</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugClient2::AddDumpInformationFile method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
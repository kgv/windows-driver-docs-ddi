---
UID: NF.winsplp.GenerateCopyFilePaths
title: GenerateCopyFilePaths
author: windows-driver-content
description: A Point and Print DLL's GenerateCopyFilePaths function is used for modifying the source and destination paths used by print spoolers when they copy print queue-associated files to a print client.
old-location: print\generatecopyfilepaths.htm
ms.assetid: 61274493-1ec4-483b-85fa-f6087cf0631e
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: Winsplp.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GenerateCopyFilePaths
req.alt-loc: Mscms.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Mscms.lib
req.dll: Mscms.dll
req.irql: 
ms.keywords: GenerateCopyFilePaths
req.iface: 
req.product: Windows 10 or later.
---

# GenerateCopyFilePaths function



## -description
<p>A Point and Print DLL's <b>GenerateCopyFilePaths</b> function is used for modifying the source and destination paths used by print spoolers when they copy print queue-associated files to a print client.</p>


## -syntax

````
DWORD GenerateCopyFilePaths(
  _In_    LPCWSTR pszPrinterName,
  _In_    LPCWSTR pszDirectory,
  _In_    LPBYTE  pSplClientInfo,
  _In_    DWORD   dwLevel,
  _Inout_ LPWSTR  pszSourceDir,
  _Inout_ LPDWORD pcchSourceDirSize,
  _Inout_ LPWSTR  pszTargetDir,
  _Inout_ LPDWORD pcchTargetDirSize,
  _In_    DWORD   dwFlags
);
````


## -parameters
<dl>

### -param <i>pszPrinterName</i> [in]

<dd>
<p>Caller-supplied pointer to a string representing the name of the print queue.</p>
</dd>

### -param <i>pszDirectory</i> [in]

<dd>
<p>Caller-supplied pointer to a string representing the value supplied for the server's <b>Directory</b> entry in the registry. For more information, see <a href="NULL">Supporting Point and Print During Printer Installations</a>.</p>
</dd>

### -param <i>pSplClientInfo</i> [in]

<dd>
<p>Caller-supplied pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff562674">SPLCLIENT_INFO_1</a> structure.</p>
</dd>

### -param <i>dwLevel</i> [in]

<dd>
<p>Caller-supplied value indicating the level number of the structure pointed to by <i>pSplClientInfo</i>. Must be 1.</p>
</dd>

### -param <i>pszSourceDir</i> [in, out]

<dd>
<p>For input, receives a caller-supplied pointer to a string representing the complete server directory path (including server name) from which files are to be copied.</p>
<p>For output, the function can modify this string.</p>
</dd>

### -param <i>pcchSourceDirSize</i> [in, out]

<dd>
<p>Caller-supplied address containing the length of the buffer pointed to by <i>pszSourceDir</i>. (Note that this is the buffer length, not the string length.)</p>
</dd>

### -param <i>pszTargetDir</i> [in, out]

<dd>
<p>For input, receives a caller-supplied pointer to a string representing the client directory path to which files are to be copied. The following rules apply:</p>
<ul>
<li>
<p>When the function is called on the server, this path is relative to PRINT$.</p>
</li>
<li>
<p>When the function is called on the client, the string contains a complete path.</p>
</li>
</ul>
<p>For output, the function can modify this string.</p>
</dd>

### -param <i>pcchTargetDirSize</i> [in, out]

<dd>
<p>Caller-supplied address containing the length of the buffer pointed to by <i>pszTargetDir</i>. (Note that this is the buffer length, not the string length.)</p>
</dd>

### -param <i>dwFlags</i> [in]

<dd>
<p>Caller-supplied flag. Can be one of the following:</p>
<p></p>
<dl>

### -param <a id="COPYFILE_FLAG_CLIENT_SPOOLER"></a><a id="copyfile_flag_client_spooler"></a>COPYFILE_FLAG_CLIENT_SPOOLER

<dd>
<p>Indicates the function is being called by the client's spooler.</p>
</dd>

### -param <a id="COPYFILE_FLAG_SERVER_SPOOLER"></a><a id="copyfile_flag_server_spooler"></a>COPYFILE_FLAG_SERVER_SPOOLER

<dd>
<p>Indicates the function is being called by the server's spooler.</p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the function should return <b>ERROR_SUCCESS</b>. Otherwise, it should return an error code defined in winerror.h.</p>

## -remarks
<p>All <a href="NULL">Point and Print DLLs</a> must export a <b>GenerateCopyFilePaths</b> function, which is called by the print spooler. Its purpose is to allow a Point and Print DLL to modify the source or destination directory path, or both, before the print spooler copies print queue-associated files from a server to a client. (The files are copied when a client connects to a print server. For a complete description of the steps involved in creating a Point and Print connection, see <a href="NULL">Supporting Point and Print</a>.)</p>

<p>A Point and Print DLL executes on both the server and the client. The <b>GenerateCopyFilePaths</b> function should check the <i>dwFlags</i> argument to determine where it is executing.</p>

<p>Typically, this function is used to provide compatibility when different versions of the operating system are executing on the client and server. For example if the function, when executing on the server, determines (by reading the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562674">SPLCLIENT_INFO_1</a> structure) that its operating system is newer than the client's, it can modify the source and destination paths to be compatible with the client's older OS. On the other hand, if the function determines that the client's operating system is newer than the client's, it should probably do nothing on the server and perform modifications, if necessary, when executing on the client.</p>

<p>Arguments for the <i>pszSourceDir</i> and <i>pszTargetDir</i> parameters point to buffers containing strings that represent the current source and destination directory paths. If modifications to either of these strings is necessary, the function should make modifications in the supplied buffers. The maximum allowable string lengths are pointed to by the <i>pcchSourceDirSize</i> and <i>pcchTargetDirSize</i> arguments.</p>

<p>If no modifications to the source or destination directories are needed, the function should just return <b>ERROR_SUCCESS</b>.</p>

<p>All <a href="NULL">Point and Print DLLs</a> must export a <b>GenerateCopyFilePaths</b> function, which is called by the print spooler. Its purpose is to allow a Point and Print DLL to modify the source or destination directory path, or both, before the print spooler copies print queue-associated files from a server to a client. (The files are copied when a client connects to a print server. For a complete description of the steps involved in creating a Point and Print connection, see <a href="NULL">Supporting Point and Print</a>.)</p>

<p>A Point and Print DLL executes on both the server and the client. The <b>GenerateCopyFilePaths</b> function should check the <i>dwFlags</i> argument to determine where it is executing.</p>

<p>Typically, this function is used to provide compatibility when different versions of the operating system are executing on the client and server. For example if the function, when executing on the server, determines (by reading the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562674">SPLCLIENT_INFO_1</a> structure) that its operating system is newer than the client's, it can modify the source and destination paths to be compatible with the client's older OS. On the other hand, if the function determines that the client's operating system is newer than the client's, it should probably do nothing on the server and perform modifications, if necessary, when executing on the client.</p>

<p>Arguments for the <i>pszSourceDir</i> and <i>pszTargetDir</i> parameters point to buffers containing strings that represent the current source and destination directory paths. If modifications to either of these strings is necessary, the function should make modifications in the supplied buffers. The maximum allowable string lengths are pointed to by the <i>pcchSourceDirSize</i> and <i>pcchTargetDirSize</i> arguments.</p>

<p>If no modifications to the source or destination directories are needed, the function should just return <b>ERROR_SUCCESS</b>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Winsplp.h (include Winsplp.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Mscms.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Mscms.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562681">SpoolerCopyFileEvent</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20GenerateCopyFilePaths function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
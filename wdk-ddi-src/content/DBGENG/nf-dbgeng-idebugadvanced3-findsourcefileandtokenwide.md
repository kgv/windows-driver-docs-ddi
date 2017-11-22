---
UID: NF.dbgeng.IDebugAdvanced3.FindSourceFileAndTokenWide
title: IDebugAdvanced3::FindSourceFileAndTokenWide
author: windows-driver-content
description: The FindSourceFileAndTokenWide method returns the filename of a source file on the source path or return the value of a variable associated with a file token.
old-location: debugger\findsourcefileandtokenwide.htm
ms.assetid: f406e755-dc46-4228-b70f-3520d3cb46a3
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
req.alt-api: IDebugAdvanced3.FindSourceFileAndTokenWide
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
ms.keywords: IDebugAdvanced3, FindSourceFileAndTokenWide, IDebugAdvanced3::FindSourceFileAndTokenWide
req.iface: IDebugAdvanced3
---

# IDebugAdvanced3::FindSourceFileAndTokenWide method



## -description
<p>The  <b>FindSourceFileAndTokenWide</b> method returns the filename of a source file on the source path or return the value of a variable associated with a file token.</p>


## -syntax

````
HRESULT FindSourceFileAndTokenWide(
  [in]            ULONG   StartElement,
  [in]            ULONG64 ModAddr,
  [in]            PCWSTR  File,
  [in]            ULONG   Flags,
  [in, optional]  PVOID   FileToken,
  [in]            ULONG   FileTokenSize,
  [out, optional] PULONG  FoundElement,
  [out, optional] PWSTR   Buffer,
  [in]            ULONG   BufferSize,
  [out, optional] PULONG  FoundSize
);
````


## -parameters
<dl>

### -param <i>StartElement</i> [in]

<dd>
<p>Specifies the index of an element within the source path to start searching from.  All elements in the source path before <i>StartElement</i> are excluded from the search.  The index of the first element is zero.  If <i>StartElement</i> is greater than or equal to the number of elements in the source path, the filing system is checked directly.</p>
<p>This parameter can be used with <i>FoundElement</i> to check for multiple matches in the source path.</p>
<p><i>StartElement</i> is ignored if the flag DEBUG_FIND_SOURCE_TOKEN_LOOKUP is set in <i>Flags</i>.</p>
</dd>

### -param <i>ModAddr</i> [in]

<dd>
<p>Specifies a location within the memory allocation of the module in the target to which the source file is related.  <i>ModAddr</i> is used for caching the search results and when querying source servers for the file.  <i>ModAddr</i> can be <b>NULL</b>.</p>
<p><i>ModAddr</i> is ignored if the flag DEBUG_FIND_SOURCE_TOKEN_LOOKUP is set in <i>Flags</i>.  And it is not used for querying source servers if <i>FileToken</i> is not <b>NULL</b>.</p>
</dd>

### -param <i>File</i> [in]

<dd>
<p>Specifies the path and filename of the file to search for.</p>
<p>If the flag DEBUG_FIND_SOURCE_TOKEN_LOOKUP is set, the file is already specified by the token in <i>FileToken</i>.  In this case, <i>File</i> specifies the name of a variable on the source server related to the file.  The variable must begin and end with the percent sign ( <b>%</b> ), for example, <b>%SRCSRVCMD%</b>.  The value of this variable is returned.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>Specifies the flags that control the behavior of this method.  For a description of these flags, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541495">DEBUG_FIND_SOURCE_XXX</a>.</p>
</dd>

### -param <i>FileToken</i> [in, optional]

<dd>
<p>Specifies a file token representing a file on a source server.  A file token can be obtained by setting <i>Which</i> to DEBUG_SRCFILE_SYMBOL_TOKEN in the method <a href="https://msdn.microsoft.com/library/windows/hardware/ff548321">GetSourceFileInformation</a>.</p>
<p>If the flag DEBUG_FIND_SOURCE_TOKEN_LOOKUP is set, <i>FileToken</i> must not be <b>NULL</b>.</p>
</dd>

### -param <i>FileTokenSize</i> [in]

<dd>
<p>Specifies the size in bytes of the <i>FileToken</i> token. If <i>FileToken</i> is <b>NULL</b>, this parameter is ignored.</p>
</dd>

### -param <i>FoundElement</i> [out, optional]

<dd>
<p>Receives the index of the element within the source path that contained the file.  If the file was found directly on the filing system (not using the source path), -1 is returned to <i>FoundElement</i>. If <i>FoundElement</i> is <b>NULL</b> or <i>Flags</i> contain DEBUG_SRCFILE_SYMBOL_TOKEN, this information is not returned.</p>
</dd>

### -param <i>Buffer</i> [out, optional]

<dd>
<p>Receives the name of the file that was found.  If the file is not on a source server, this is the name of the file in the local source cache.  If the flag DEBUG_FIND_SOURCE_FULL_PATH is set, this is the full canonical path name for the file.  Otherwise, it is the concatenation of the directory in the source path with the tail of <i>File</i> that was used to find the file.</p>
<p>If the flag DEBUG_SRCFILE_SYMBOL_TOKEN is set in <i>Flags</i>, <i>Buffer</i> receives the value of the variable named <i>File</i> associated with the file token <i>FileToken</i>.</p>
<p>If <i>Buffer</i> is <b>NULL</b>, this information is not returned.</p>
</dd>

### -param <i>BufferSize</i> [in]

<dd>
<p>Specifies the size in characters of the <i>Buffer</i> buffer. If <i>Buffer</i> is <b>NULL</b>, this parameter is ignored.</p>
</dd>

### -param <i>FoundSize</i> [out, optional]

<dd>
<p>Specifies the size in characters of the name of the file.  If <i>foundSize</i> is <b>NULL</b>, this information is not returned.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>S_FALSE</b></dt>
</dl><p>The method was successful.  However, the <i>Buffer</i> buffer was too small to hold the file name or variable value, so the string was truncated to fit in the buffer.</p>

<p> </p>

## -remarks
<p>When the flag DEBUG_SRCFILE_SYMBOL_TOKEN is set in <i>Flags</i>, this method does not search for a file on the source path.  Instead, it looks up a variable associated with the file token provided in <i>FileToken</i>.  These variables are documented in the topic <a href="https://msdn.microsoft.com/library/windows/hardware/ff551958">Language Specification 1</a>.  For example, to retrieve the value of the variable SRCSRVCMD--the command to extract the source file from source control (also returned by the DEBUG_SRCFILE_SYMBOL_TOKEN_SOURCE_COMMAND_WIDE function of <a href="https://msdn.microsoft.com/library/windows/hardware/ff548321">GetSourceFileInformation</a>)--set <i>File</i> to <b>%SRCSRVCMD%</b>.</p>

<p>The engine uses the following steps--in order--to search for the file:  </p>

<p>If the source path contains any source servers and the flag DEBUG_FIND_SOURCE_NO_SRCSRV is not set, the source server in the source path is searched first.</p>

<p>The first match found is returned.</p>

<p>For each directory in the source path, an attempt is made to find an overlap between the end of the directory path and the beginning of the file path.  For example, if the source path contains a directory C:\a\b\c\d and <i>File</i> is c\d\e\foo.c, the file C:\a\b\c\d\e\foo.c is a match.</p>

<p>If the flag DEBUG_FIND_SOURCE_BEST_MATCH is set, the match with the longest overlap is returned; otherwise, the first match is returned.</p>

<p>For each directory in the source path, <i>File</i> is appended to the directory.  If no match is found, this process is repeated and each time the first directory is removed from the beginning of the file path.  For example, if the source path contains a directory C:\a\b and <i>File</i> is c\d\e\foo.c, the file C:\a\b\e\foo.c is a match.</p>

<p>The first match found is returned.</p>

<p>The file <i>File</i> is looked up directly on the filing system.</p>

<p>For more information about source files, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff560141">Using Source Files</a>.  For an overview of the source path and its syntax, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff556906">Source Path</a>.</p>

<p>When the flag DEBUG_SRCFILE_SYMBOL_TOKEN is set in <i>Flags</i>, this method does not search for a file on the source path.  Instead, it looks up a variable associated with the file token provided in <i>FileToken</i>.  These variables are documented in the topic <a href="https://msdn.microsoft.com/library/windows/hardware/ff551958">Language Specification 1</a>.  For example, to retrieve the value of the variable SRCSRVCMD--the command to extract the source file from source control (also returned by the DEBUG_SRCFILE_SYMBOL_TOKEN_SOURCE_COMMAND_WIDE function of <a href="https://msdn.microsoft.com/library/windows/hardware/ff548321">GetSourceFileInformation</a>)--set <i>File</i> to <b>%SRCSRVCMD%</b>.</p>

<p>The engine uses the following steps--in order--to search for the file:  </p>

<p>If the source path contains any source servers and the flag DEBUG_FIND_SOURCE_NO_SRCSRV is not set, the source server in the source path is searched first.</p>

<p>The first match found is returned.</p>

<p>For each directory in the source path, an attempt is made to find an overlap between the end of the directory path and the beginning of the file path.  For example, if the source path contains a directory C:\a\b\c\d and <i>File</i> is c\d\e\foo.c, the file C:\a\b\c\d\e\foo.c is a match.</p>

<p>If the flag DEBUG_FIND_SOURCE_BEST_MATCH is set, the match with the longest overlap is returned; otherwise, the first match is returned.</p>

<p>For each directory in the source path, <i>File</i> is appended to the directory.  If no match is found, this process is repeated and each time the first directory is removed from the beginning of the file path.  For example, if the source path contains a directory C:\a\b and <i>File</i> is c\d\e\foo.c, the file C:\a\b\e\foo.c is a match.</p>

<p>The first match found is returned.</p>

<p>The file <i>File</i> is looked up directly on the filing system.</p>

<p>For more information about source files, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff560141">Using Source Files</a>.  For an overview of the source path and its syntax, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff556906">Source Path</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549807">IDebugAdvanced3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545423">FindSourceFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541495">DEBUG_FIND_SOURCE_XXX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548321">GetSourceFileInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548367">GetSourcePathElement</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugAdvanced3::FindSourceFileAndTokenWide method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
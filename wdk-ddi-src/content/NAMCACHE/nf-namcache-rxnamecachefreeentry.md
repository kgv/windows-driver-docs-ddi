---
UID: NF.namcache.RxNameCacheFreeEntry
title: RxNameCacheFreeEntry
author: windows-driver-content
description: RxNameCacheFreeEntry releases the storage for a NAME_CACHE entry and decrements the count of the NAME_CACHE cache entries associated with a NAME_CACHE_CONTROL structure.
old-location: ifsk\rxnamecachefreeentry.htm
ms.assetid: c1adef80-b8f2-49bb-9254-b89c8d1af220
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: namcache.h
req.include-header: Namcache.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxNameCacheFreeEntry
req.alt-loc: namcache.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: RxNameCacheFreeEntry
req.iface: 
---

# RxNameCacheFreeEntry function



## -description
<p><b>RxNameCacheFreeEntry</b> releases the storage for a NAME_CACHE entry and decrements the count of the NAME_CACHE cache entries associated with a NAME_CACHE_CONTROL structure. </p>


## -syntax

````
VOID RxNameCacheFreeEntry(
  _In_ PNAME_CACHE_CONTROL NameCacheCtl,
  _In_ PNAME_CACHE         NameCache
);
````


## -parameters
<dl>

### -param <i>NameCacheCtl</i> [in]

<dd>
<p>A pointer to the NAME_CACHE_CONTROL structure for the name cache.</p>
</dd>

### -param <i>NameCache</i> [in]

<dd>
<p>A pointer to the NAME_CACHE structure to free.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The <b>RxNameCacheFreeEntry</b> routine assumes that the name cache entry is not on either the free or active list.</p>

<p>The <b>RxNameCacheFreeEntry</b> routine frees memory allocated for the name buffer if the name buffer for this name cache entry is not <b>NULL</b>. This routine will then free memory used for the NAME_CACHE entry. Then, the count of name cache entries on <i>NameCacheCtl</i> is decremented.</p>

<p>The <b>RxNameCacheFreeEntry</b> routine assumes that the name cache entry is not on either the free or active list.</p>

<p>The <b>RxNameCacheFreeEntry</b> routine frees memory allocated for the name buffer if the name buffer for this name cache entry is not <b>NULL</b>. This routine will then free memory used for the NAME_CACHE entry. Then, the count of name cache entries on <i>NameCacheCtl</i> is decremented.</p>

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
<dt>Namcache.h (include Namcache.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554552">RxNameCacheActivateEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554558">RxNameCacheCheckEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554565">RxNameCacheCreateEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554569">RxNameCacheExpireEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554570">RxNameCacheExpireEntryWithShortName</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554573">RxNameCacheFetchEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554575">RxNameCacheFinalize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554586">RxNameCacheInitialize</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxNameCacheFreeEntry function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
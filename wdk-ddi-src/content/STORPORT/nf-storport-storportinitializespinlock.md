---
UID: NF.storport.StorPortInitializeSpinlock
title: StorPortInitializeSpinlock
author: windows-driver-content
description: The StorPortInitializeSpinLock routine initializes a variable of type STOR_KSPIN_LOCK.
old-location: storage\storportinitializespinlock.htm
ms.assetid: 150B1ED3-572A-4986-BED6-628ED6C54CCF
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortInitializeSpinlock
req.alt-loc: storport.h
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
ms.keywords: StorPortInitializeSpinlock
req.iface: 
req.product: Windows 10 or later.
---

# StorPortInitializeSpinlock function



## -description
<p class="CCE_Message">[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]</p>
<p>The <b>StorPortInitializeSpinLock </b>routine initializes a variable of type <b>STOR_KSPIN_LOCK</b>.</p>


## -syntax

````
ULONG StorPortInitializeSpinlock(
  _In_  PVOID            HwDeviceExtension,
  _Out_ PSTOR_KSPIN_LOCK Lock
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension for the host bus adapter (HBA).</p>
</dd>

### -param <i>Lock</i> [out]

<dd>
<p>Pointer to a spin lock of type <b>STOR_KSPIN_LOCK</b>, for which the caller must provide the storage</p>
</dd>
</dl>

## -returns
<p><b>StorPortInitializeSpinlock</b> returns one of the following status codes:</p><dl>
<dt><b>STOR_STATUS_NOT_IMPLEMENTED</b></dt>
</dl><p>This function is not implemented on the active operating system.</p><dl>
<dt><b>STOR_STATUS_SUCCESS</b></dt>
</dl><p>The list items were removed successfully or the list is already empty.</p><dl>
<dt><b>STOR_STATUS_INVALID_PARAMETER</b></dt>
</dl><p>A pointer in <i>ListHead</i> or <i>Result</i> is <b>NULL</b>.</p>

<p> </p>

## -remarks
<p>This routine must be called before an initial call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff567025">StorPortAcquireSpinLock</a>, to any other support routine that requires a spin lock as an argument.</p>

<p>For more information about spin locks, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563830">Spin Locks</a>.</p>

<p>This routine must be called before an initial call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff567025">StorPortAcquireSpinLock</a>, to any other support routine that requires a spin lock as an argument.</p>

<p>For more information about spin locks, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563830">Spin Locks</a>.</p>

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
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567025">StorPortAcquireSpinLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567023">StorPortAcquireMSISpinLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567496">StorPortReleaseSpinLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567494">StorPortReleaseMSISpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortInitializeSpinlock routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
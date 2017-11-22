---
UID: NF.dmusicks.ISynthSinkDMus.SyncToMaster
title: ISynthSinkDMus::SyncToMaster
author: windows-driver-content
description: The SyncToMaster method allows synchronization to the master clock in order to avoid drift.
old-location: audio\isynthsinkdmus_synctomaster.htm
ms.assetid: 5009e4d8-5299-4eeb-a70d-5be87694b1d0
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: audio
req.header: dmusicks.h
req.include-header: Dmusicks.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ISynthSinkDMus.SyncToMaster
req.alt-loc: dmusicks.h
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
ms.keywords: ISynthSinkDMus, SyncToMaster, ISynthSinkDMus::SyncToMaster
req.iface: ISynthSinkDMus
---

# ISynthSinkDMus::SyncToMaster method



## -description
<p>The <code>SyncToMaster</code> method allows synchronization to the master clock in order to avoid drift.</p>


## -syntax

````
NTSTATUS SyncToMaster(
  [in] REFERENCE_TIME rtTime,
  [in] BOOL           fStart
);
````


## -parameters
<dl>

### -param <i>rtTime</i> [in]

<dd>
<p>Specifies the reference time from the master clock. Reference time is measured in 100-nanosecond units.</p>
</dd>

### -param <i>fStart</i> [in]

<dd>
<p>Specifies whether the sample clock is to be reset to zero with this reference time. If <b>TRUE</b>, the sample clock must be reset to zero at time <i>rtTime</i>. If <b>FALSE</b>, the sample clock is not reset.</p>
</dd>
</dl>

## -returns
<p><code>SyncToMaster</code> returns STATUS_SUCCESS if the call was successful. Otherwise, the method returns an appropriate error code.</p>

## -remarks
<p>Because the master time and sample time might be driven by different crystals, they can drift apart. The port driver periodically calls this method to give the miniport driver an opportunity to synchronize its sample clock to the master clock.</p>

<p>Parameter <i>fStart</i> is <b>TRUE</b> during the first call to <code>SyncToMaster</code> after the stream enters the KSSTATE_RUN state (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff566856">KSSTATE</a>). Otherwise, <i>fStart</i> is <b>FALSE</b>.</p>

<p>Because the master time and sample time might be driven by different crystals, they can drift apart. The port driver periodically calls this method to give the miniport driver an opportunity to synchronize its sample clock to the master clock.</p>

<p>Parameter <i>fStart</i> is <b>TRUE</b> during the first call to <code>SyncToMaster</code> after the stream enters the KSSTATE_RUN state (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff566856">KSSTATE</a>). Otherwise, <i>fStart</i> is <b>FALSE</b>.</p>

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
<dt>Dmusicks.h (include Dmusicks.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566856">KSSTATE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20ISynthSinkDMus::SyncToMaster method%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
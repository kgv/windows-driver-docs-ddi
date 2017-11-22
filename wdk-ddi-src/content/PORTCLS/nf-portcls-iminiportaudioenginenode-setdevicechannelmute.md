---
UID: NF.portcls.IMiniportAudioEngineNode.SetDeviceChannelMute
title: IMiniportAudioEngineNode::SetDeviceChannelMute
author: windows-driver-content
description: Sets the state of the Mute node for the audio device channel.
old-location: audio\iminiportaudioenginenode_setdevicechannelmute.htm
ms.assetid: 272B83D4-AACE-419D-9DD7-A1AE1C8A931A
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: audio
req.header: portcls.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IMiniportAudioEngineNode.SetDeviceChannelMute
req.alt-loc: Portcls.h
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
ms.keywords: IMiniportAudioEngineNode, SetDeviceChannelMute, IMiniportAudioEngineNode::SetDeviceChannelMute
req.iface: IMiniportAudioEngineNode
---

# IMiniportAudioEngineNode::SetDeviceChannelMute method



## -description
<p>Sets the state of the Mute node for the audio device channel.</p>


## -syntax

````
NTSTATUS SetDeviceChannelMute(
  [in] ULONG  ulNodeId,
  [in] UINT32 ulChannel,
  [in] BOOL   bMute
);
````


## -parameters
<dl>

### -param <i>ulNodeId</i> [in]

<dd>
<p>The ID for the node that represents the audio device.</p>
</dd>

### -param <i>ulChannel</i> [in]

<dd>
<p>The audio device channel.</p>
</dd>

### -param <i>bMute</i> [in]

<dd>
<p>The state to which the Mute node for the audio device channel will be set.</p>
</dd>
</dl>

## -returns
<p><b>SetDeviceChannelMute</b> returns S_OK, if the call was successful. Otherwise, the method returns an appropriate error 

code.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
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
<dt>Portcls.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn302040">IMiniportAudioEngineNode</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20IMiniportAudioEngineNode::SetDeviceChannelMute method%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
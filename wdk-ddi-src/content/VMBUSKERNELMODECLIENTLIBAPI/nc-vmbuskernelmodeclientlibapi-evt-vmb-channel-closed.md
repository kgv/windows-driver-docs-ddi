---
UID: NC.vmbuskernelmodeclientlibapi.EVT_VMB_CHANNEL_CLOSED
title: EVT_VMB_CHANNEL_CLOSED
author: windows-driver-content
description: The EvtVmbChannelClosed callback function is invoked when the client endpoint in the guest virtual machine closes a channel by using the VmbChannelDisable function, or the opposite endpoint rescinds or closes the channel.
old-location: netvista\evt_vmb_channel_closed.htm
ms.assetid: 457FADB8-4126-43A8-AA38-E3D722728459
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: vmbuskernelmodeclientlibapi.h
req.include-header: VmbusKernelModeClientLibApi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PFN_VMB_CHANNEL_CLOSED
req.alt-loc: VmbusKernelModeClientLibApi.h
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
ms.keywords: VideoPortGetAgpServices
req.iface: 
req.product: Windows 10 or later.
---

# EVT_VMB_CHANNEL_CLOSED callback



## -description
<p class="CCE_Message">[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]</p>
<p>The <i>EvtVmbChannelClosed</i> callback function is invoked when the client endpoint in the guest virtual machine closes a
channel by using the <a href="https://msdn.microsoft.com/688A1DF3-F801-47C3-8403-9FA5D96BD428">VmbChannelDisable</a> function, or the opposite endpoint rescinds or closes the 
channel.  </p>


## -prototype

````
EVT_VMB_CHANNEL_CLOSED EvtVmbChannelClosed;

VOID EvtVmbChannelClosed(
  _In_ VMBCHANNEL Channel
)
{ ... }

typedef EVT_VMB_CHANNEL_CLOSED PFN_VMB_CHANNEL_CLOSED;
````


## -parameters
<dl>

### -param <i>Channel</i> [in]

<dd>
<p>The channel that the guest virtual machine closes.</p>
</dd>
</dl>

## -returns
<p>This callback function does not return a value.</p>

## -remarks
<p>After a channel is created, a client driver can specify callback functions for state changes, including  <i>EvtVmbChannelClosed</i>, by using the <a href="https://msdn.microsoft.com/2255C8A2-85FB-4B96-8AE9-66FAFD73EE73">VMB_CHANNEL_STATE_CHANGE_CALLBACKS_INIT</a> function.</p>

<p>After this callback function finishes on the host, the channel 
is either closed or disabled, depending on whether the guest closed 
the channel or the Kernel Mode Client Library (KMCL) client called <a href="https://msdn.microsoft.com/688A1DF3-F801-47C3-8403-9FA5D96BD428">VmbChannelDisable</a>, 
respectively.  </p>

<p>On the guest, the channel always becomes disabled. It 
must be restarted by using the <a href="https://msdn.microsoft.com/A0256B3F-C35C-45AB-A825-0A82189F08DC">VmbChannelEnable</a> function.  </p>

<p>After this  is function invoked, packets can be queued, but they cannot be sent.</p>

<p>After a channel is created, a client driver can specify callback functions for state changes, including  <i>EvtVmbChannelClosed</i>, by using the <a href="https://msdn.microsoft.com/2255C8A2-85FB-4B96-8AE9-66FAFD73EE73">VMB_CHANNEL_STATE_CHANGE_CALLBACKS_INIT</a> function.</p>

<p>After this callback function finishes on the host, the channel 
is either closed or disabled, depending on whether the guest closed 
the channel or the Kernel Mode Client Library (KMCL) client called <a href="https://msdn.microsoft.com/688A1DF3-F801-47C3-8403-9FA5D96BD428">VmbChannelDisable</a>, 
respectively.  </p>

<p>On the guest, the channel always becomes disabled. It 
must be restarted by using the <a href="https://msdn.microsoft.com/A0256B3F-C35C-45AB-A825-0A82189F08DC">VmbChannelEnable</a> function.  </p>

<p>After this  is function invoked, packets can be queued, but they cannot be sent.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>VmbusKernelModeClientLibApi.h (include VmbusKernelModeClientLibApi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/2255C8A2-85FB-4B96-8AE9-66FAFD73EE73">VMB_CHANNEL_STATE_CHANGE_CALLBACKS_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/688A1DF3-F801-47C3-8403-9FA5D96BD428">VmbChannelDisable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/A0256B3F-C35C-45AB-A825-0A82189F08DC">VmbChannelEnable</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20EVT_VMB_CHANNEL_CLOSED callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
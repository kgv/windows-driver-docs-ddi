---
UID: NF:portcls.IMiniportStreamAudioEngineNode.GetStreamAttributeSteppings
title: IMiniportStreamAudioEngineNode::GetStreamAttributeSteppings method
author: windows-driver-content
description: Gets the allowed stepping value for the audio stream attribute.
old-location: audio\iminiportstreamaudioenginenode_getstreamattributesteppings.htm
old-project: audio
ms.assetid: 2EC0C859-5479-4A55-9180-DB9938400DF7
ms.author: windowsdriverdev
ms.date: 3/19/2018
ms.keywords: GetStreamAttributeSteppings method [Audio Devices], GetStreamAttributeSteppings method [Audio Devices], IMiniportStreamAudioEngineNode interface, GetStreamAttributeSteppings,IMiniportStreamAudioEngineNode.GetStreamAttributeSteppings, IMiniportStreamAudioEngineNode, IMiniportStreamAudioEngineNode interface [Audio Devices], GetStreamAttributeSteppings method, IMiniportStreamAudioEngineNode::GetStreamAttributeSteppings, audio.iminiportstreamaudioenginenode_getstreamattributesteppings, portcls/IMiniportStreamAudioEngineNode::GetStreamAttributeSteppings
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: portcls.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	COM
api_location:
-	Portcls.h
api_name:
-	IMiniportStreamAudioEngineNode.GetStreamAttributeSteppings
product:
- Windows
targetos: Windows
req.typenames: PC_EXIT_LATENCY, *PPC_EXIT_LATENCY
---

# IMiniportStreamAudioEngineNode::GetStreamAttributeSteppings method


## -description


Gets the allowed stepping value for the audio stream attribute.


## -parameters




### -param targetType [in]

An <a href="https://msdn.microsoft.com/library/windows/hardware/dn302034">eChannelTargetType</a> enumerated value that specifies the  target node type.


### -param pKsPropStepLong [out]

A structure of type <a href="http://msdn.microsoft.com/en-us/library/windows/hardware/ff565631(v=vs.85).aspx">KSPROPERTY_STEPPING_LONG</a> that contains information about the allowed stepping value for the audio stream attribute.


### -param ui32DataSize [in]

The allowed stepping value.


## -returns



<b>GetStreamAttributeSteppings</b> returns S_OK, if the call was successful. Otherwise, the method returns an appropriate error 

code.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/dn265090">IMiniportStreamAudioEngineNode</a>



<a href="http://msdn.microsoft.com/en-us/library/windows/hardware/ff565631(v=vs.85).aspx">KSPROPERTY_STEPPING_LONG</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/dn302034">eChannelTargetType</a>
 

 


---
UID: NF:ksproxy.IKsControl.KsProperty
title: IKsControl::KsProperty method
author: windows-driver-content
description: The KsProperty method sets a property or retrieves property information, along with any other defined support operations available on a property set.
old-location: stream\ikscontrol_ksproperty.htm
old-project: stream
ms.assetid: cc43f704-e1f8-4d62-8cdf-11575ec0b473
ms.author: windowsdriverdev
ms.date: 2/23/2018
ms.keywords: IKsControl, IKsControl interface [Streaming Media Devices], KsProperty method, IKsControl::KsProperty, KsProperty method [Streaming Media Devices], KsProperty method [Streaming Media Devices], IKsControl interface, KsProperty,IKsControl.KsProperty, ksproxy/IKsControl::KsProperty, ksproxy_463b7e97-4356-4d2e-b005-6f81219bda64.xml, stream.ikscontrol_ksproperty
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: ksproxy.h
req.include-header: Ksproxy.h
req.target-type: DesktopMobile
req.target-min-winverclnt: 
req.target-min-winversvr: 
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
-	ksproxy.h
api_name:
-	IKsControl.KsProperty
product:
- Windows
targetos: Windows
req.typenames: PIPE_STATE
---

# IKsControl::KsProperty method


## -description


The <b>KsProperty</b> method sets a property or retrieves property information, along with any other defined support operations available on a property set. 


## -parameters




### -param Property [in]

Pointer to a structure that describes a property and the request type of the property request. This structure must be either a <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a> or a structure that contains a <b>KSPROPERTY</b> structure as its first member. An example of a structure that can be pointed to by this member is the <a href="https://msdn.microsoft.com/library/windows/hardware/ff566089">KSPROPERTY_VIDEOPROCAMP_S</a> structure.


### -param PropertyLength [in]

Size, in bytes, of the buffer at <i>Property</i>.


### -param PropertyData [in, out]

Pointer to a buffer that contains data for a KSPROPERTY_TYPE_SET, KSPROPERTY_TYPE_UNSERIALIZESET, or KSPROPERTY_TYPE_UNSERIALIZERAW operation, or buffer space that receives data for all other operations.


### -param DataLength [in]

Size, in bytes, of the buffer at <i>PropertyData</i>.


### -param BytesReturned [in, out]

Pointer to a variable that receives the size, in bytes, of the data that <b>KsProperty</b> stores in the buffer at <i>PropertyData</i>. If no data is stored, the size is zero.


## -returns



Returns NOERROR if successful; otherwise, returns an error code.




## -remarks



To determine the buffer size that is required for a specific property request, you can call this method with <i>PropertyData</i> set to <b>NULL</b> and <i>DataLength</i> equal to zero. The method returns HRESULT_FROM_WIN32(ERROR_MORE_DATA), and <i>BytesReturned</i> contains the size of the required buffer.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff566089">KSPROPERTY_VIDEOPROCAMP_S</a>
 

 


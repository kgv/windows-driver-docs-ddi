---
UID: NF:engextcpp.ExtRemoteData.GetDouble
title: ExtRemoteData::GetDouble method
author: windows-driver-content
description: The GetDouble method returns a double version of the ExtRemoteData object, which represents the contents of the target's memory.
old-location: debugger\extremotedata_getdouble.htm
old-project: debugger
ms.assetid: f8645e92-659f-42b8-a850-49a434ec2a67
ms.author: windowsdriverdev
ms.date: 3/26/2018
ms.keywords: EngExtCpp_Ref_8776e6fd-9e13-4502-a445-da65a8fcfe41.xml, ExtRemoteData, ExtRemoteData class [Windows Debugging], GetDouble method, ExtRemoteData::GetDouble, GetDouble method [Windows Debugging], GetDouble method [Windows Debugging], ExtRemoteData class, GetDouble,ExtRemoteData.GetDouble, debugger.extremotedata_getdouble
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: engextcpp.hpp
req.include-header: Engextcpp.hpp
req.target-type: Desktop
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
-	engextcpp.hpp
api_name:
-	ExtRemoteData.GetDouble
product:
- Windows
targetos: Windows
req.typenames: SILO_DRIVER_CAPABILITIES, *PSILO_DRIVER_CAPABILITIES
---

# ExtRemoteData::GetDouble method


## -description


The <b>GetDouble</b> method returns a <b>double</b> version of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544008">ExtRemoteData</a> object, which represents the contents of the target's memory.


## -parameters






## -returns



<b>GetDouble</b> returns the <b>double</b> version of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544008">ExtRemoteData</a> object.




## -remarks



The size of the memory represented by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544008">ExtRemoteData</a> object must be <code>sizeof(double)</code>.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff544008">ExtRemoteData</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff544019">ExtRemoteData::GetData</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff544028">ExtRemoteData::GetFloat</a>
 

 


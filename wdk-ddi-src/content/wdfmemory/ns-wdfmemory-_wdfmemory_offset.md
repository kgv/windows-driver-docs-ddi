---
UID: NS:wdfmemory._WDFMEMORY_OFFSET
title: "_WDFMEMORY_OFFSET"
author: windows-driver-content
description: The WDFMEMORY_OFFSET structure identifies a subsection of a memory object's buffer.
old-location: wdf\wdfmemory_offset.htm
old-project: wdf
ms.assetid: ca891a21-e7ab-4230-bfc4-adfdb413838b
ms.author: windowsdriverdev
ms.date: 2/26/2018
ms.keywords: "*PWDFMEMORY_OFFSET, DFMemoryObjectRef_d6ea5bd1-f672-4624-9663-f1e5f70eb8b2.xml, PWDFMEMORY_OFFSET, PWDFMEMORY_OFFSET structure pointer, WDFMEMORY_OFFSET, WDFMEMORY_OFFSET structure, _WDFMEMORY_OFFSET, kmdf.wdfmemory_offset, wdf.wdfmemory_offset, wdfmemory/PWDFMEMORY_OFFSET, wdfmemory/WDFMEMORY_OFFSET"
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wdfmemory.h
req.include-header: Wdf.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
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
-	HeaderDef
api_location:
-	wdfmemory.h
api_name:
-	WDFMEMORY_OFFSET
product:
- Windows
targetos: Windows
req.typenames: WDFMEMORY_OFFSET, *PWDFMEMORY_OFFSET
req.product: Windows 10 or later.
---

# _WDFMEMORY_OFFSET structure


## -description


<p class="CCE_Message">[Applies to KMDF and UMDF]

The <b>WDFMEMORY_OFFSET</b> structure identifies a subsection of a memory object's buffer.


## -struct-fields




### -field BufferOffset

A byte offset from the beginning of the memory object's buffer. This offset identifies the location of the buffer's subsection. A value of zero represents the beginning of the buffer.


### -field BufferLength

The length, in bytes, of the buffer's subsection. A value of zero represents the entire buffer.


## -remarks



The <b>WDFMEMORY_OFFSET</b> structure is used as a member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552392">WDF_MEMORY_DESCRIPTOR</a> structure and as an input parameter to various I/O target object methods.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff552392">WDF_MEMORY_DESCRIPTOR</a>
 

 


---
UID: NS:ntdddisk._SENDCMDINPARAMS
title: "_SENDCMDINPARAMS"
author: windows-driver-content
description: The SENDCMDINPARAMS structure contains the input parameters for the SMART_SEND_DRIVE_COMMAND request.
old-location: storage\sendcmdinparams.htm
old-project: storage
ms.assetid: 4c02da7e-2d93-4e0c-9666-acb380c6d39a
ms.author: windowsdriverdev
ms.date: 3/29/2018
ms.keywords: "*LPSENDCMDINPARAMS, *PSENDCMDINPARAMS, LPSENDCMDINPARAMS, LPSENDCMDINPARAMS structure pointer [Storage Devices], PSENDCMDINPARAMS, PSENDCMDINPARAMS structure pointer [Storage Devices], SENDCMDINPARAMS, SENDCMDINPARAMS structure [Storage Devices], _SENDCMDINPARAMS, ntdddisk/LPSENDCMDINPARAMS, ntdddisk/PSENDCMDINPARAMS, ntdddisk/SENDCMDINPARAMS, storage.sendcmdinparams, structs-IDE_b80faf9d-dfcf-4eac-b0be-fb18964c4c2b.xml"
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ntdddisk.h
req.include-header: Ntdddisk.h
req.target-type: Windows
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
-	HeaderDef
api_location:
-	ntdddisk.h
api_name:
-	SENDCMDINPARAMS
product:
- Windows
targetos: Windows
req.typenames: SENDCMDINPARAMS, *PSENDCMDINPARAMS, *LPSENDCMDINPARAMS
---

# _SENDCMDINPARAMS structure


## -description


The SENDCMDINPARAMS structure contains the input parameters for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff566206">SMART_SEND_DRIVE_COMMAND</a> request.


## -struct-fields




### -field cBufferSize

Contains the buffer size, in bytes.


### -field irDriveRegs

Contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff559015">IDEREGS</a> structure used to report the contents of the IDE controller registers.


### -field bDriveNumber

The <b>bDriveNumber</b> member is opaque. Do not use it. The operating system ignores this member, because the physical drive that receives the request depends on the handle that the caller uses when making the request.


### -field bReserved

Reserved. 


### -field dwReserved

Reserved. 


### -field bBuffer

Pointer to the input buffer. 


## -remarks



The <a href="https://msdn.microsoft.com/library/windows/hardware/ff566206">SMART_SEND_DRIVE_COMMAND</a> is used to send a Self-Monitoring Analysis and Reporting Technology (SMART) commands to a device. 

The SENDCMDINPARAMS structure is also used with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff566204">SMART_RCV_DRIVE_DATA</a> request. 




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff565405">SENDCMDOUTPARAMS</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff566204">SMART_RCV_DRIVE_DATA</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff566206">SMART_SEND_DRIVE_COMMAND</a>
 

 


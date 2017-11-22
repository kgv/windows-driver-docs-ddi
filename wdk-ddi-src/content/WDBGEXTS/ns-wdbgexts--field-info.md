---
UID: NS.wdbgexts._FIELD_INFO
title: FIELD_INFO
author: windows-driver-content
description: The FIELD_INFO structure is used by the IG_DUMP_SYMBOL_INFOIoctl operation to provide information about a member in a structure.
old-location: debugger\field_info.htm
ms.assetid: 627b14dc-9b13-464c-ba23-6e91bef2b940
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: debugger
req.header: wdbgexts.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FIELD_INFO
req.alt-loc: WdbgExts.h
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
ms.keywords: FIELD_INFO, FIELD_INFO, *PFIELD_INFO
req.iface: 
req.product: Windows 10 or later.
---

# FIELD_INFO structure



## -description
<p>The <b>FIELD_INFO</b> structure is used by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550906">IG_DUMP_SYMBOL_INFO</a>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551084">Ioctl</a> operation to provide information about a member in a structure.</p>


## -syntax

````
typedef struct _FIELD_INFO {
  PUCHAR           fName;
  PUCHAR           printName;
  ULONG            size;
  ULONG            fOptions;
  ULONG64          address;
  union {
    PVOID fieldCallBack;
    PVOID pBuffer;
  };
  ULONG            TypeId;
  ULONG            FieldOffset;
  ULONG            BufferSize;
  struct _BitField {
    USHORT Position;
    USHORT Size;
  } BitField;
  ULONG            fPointer  :2;
  ULONG            fArray  :1;
  ULONG            fStruct  :1;
  ULONG            fConstant  :1;
  ULONG            Reserved  :27;
} FIELD_INFO, *PFIELD_INFO;
````


## -struct-fields
<dl>

### -field <b>fName</b>

<dd>
<p>Specifies the name of the symbol's member to which this structure applies.  Submembers can be specified using the delimiters "<b>.</b>" and "<b>-&gt;</b>".  Unless DBG_DUMP_FIELD_FULL_NAME is set in <b>fOptions</b>, <b>fName</b> is considered to be the beginning of the member name.</p>
</dd>

### -field <b>printName</b>

<dd>
<p>Specifies an alternative name to use when printing the name of the member.  If <b>printName</b> is <b>NULL</b>, the actual name of the member is used when printing the name of the member.</p>
</dd>

### -field <b>size</b>

<dd>
<p>Receives the size in the target's memory, in bytes, of the member that is specified by <b>fName</b>.</p>
<p>If the member is an array, <b>size</b> specifies the number of elements in the array.</p>
</dd>

### -field <b>fOptions</b>

<dd>
<p>Specifies the flags that determine the behavior of the IG_DUMP_SYMBOL_INFO <b>Ioctl</b> operation.  For a description of these flags, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff540429">DBG_DUMP_FIELD_XXX</a>.</p>
</dd>

### -field <b>address</b>

<dd>
<p>Receives the address in the target's memory of the member that is specified by <b>fName</b>.  If no address is supplied for the symbol type in SYM_DUMP_PARAM.<b>addr</b>, <b>address</b> receives the offset of the member relative to the beginning of an instance of the type.  For more information about SYM_DUMP_PARAM, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff550906">IG_DUMP_SYMBOL_INFO</a>.</p>
</dd>

### -field <b>fieldCallBack</b>

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff553487">PSYM_DUMP_FIELD_CALLBACK</a> callback function to be called with the information about the member that is specified by <b>fName</b>.  The callback function is passed a structure with the field information and the value of SYM_DUMP_PARAM.<b>context</b>.</p>
<p>No callback function is called if DBG_DUMP_FIELD_NO_CALLBACK_REQ is set in <b>fOptions</b>, <b>fieldCallBack</b> is <b>NULL</b>, or the <b>Options</b> member of the SYM_DUMP_PARAM structure passed to <b>Ioctl</b> does not have DBG_DUMP_CALL_FOR_EACH set.  If DBG_DUMP_FIELD_COPY_FIELD_DATA is set in <b>fOptions</b>, <b>fieldCallBack</b> is not used.</p>
</dd>

### -field <b>pBuffer</b>

<dd>
<p>Specifies a buffer to receive the value of the member specified by <b>fName</b>.  This member is only used if DBG_DUMP_FIELD_COPY_FIELD_DATA is set in <b>fOptions</b>.</p>
</dd>

### -field <b>TypeId</b>

<dd>
<p>Receives the identifier for the type of the member that is specified by <b>fName</b>.</p>
</dd>

### -field <b>FieldOffset</b>

<dd>
<p>Receives the offset of the member within the structure.</p>
</dd>

### -field <b>BufferSize</b>

<dd>
<p>Specifies the size, in bytes, of the <b>pBuffer</b> buffer.</p>
</dd>

### -field <b>BitField</b>

<dd>
<p>Receives information about bit fields in a structure.
      
	 </p>
<dl>

### -field <b>Position</b>

<dd>
<p>Receives the start position of the bit field.  This is the number of bits from to the beginning of the structure to the bit field.</p>
</dd>

### -field <b>Size</b>

<dd>
<p>Receives the size, in bits, of the bit field.</p>
</dd>
</dl>
</dd>

### -field <b>fPointer</b>

<dd>
<p>Receives a Boolean value that indicates whether the member is a pointer.  <b>fPointer</b> is <b>FALSE</b> if the member is not a pointer.  It is 1 if the member is a 32-bit pointer and 3 if the member is a 64-bit pointer.</p>
</dd>

### -field <b>fArray</b>

<dd>
<p>Receives a Boolean value that indicates whether the member is an array.  <b>fArray</b> is <b>FALSE</b> if the field is not an array and <b>TRUE</b> if it is.</p>
</dd>

### -field <b>fStruct</b>

<dd>
<p>Receives a Boolean value that indicates whether the member is a structure.  <b>fStruct</b> is <b>FALSE</b> if the member is not a structure and <b>TRUE</b> if it is.</p>
</dd>

### -field <b>fConstant</b>

<dd>
<p>Receives a Boolean value that indicates whether the member is a constant.  <b>fConstant</b> is <b>FALSE</b> if the member is not a constant and <b>TRUE</b> if it is.</p>
</dd>

### -field <b>Reserved</b>

<dd></dd>
</dl>

## -remarks
<p>When calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550906">IG_DUMP_SYMBOL_INFO</a>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551084">Ioctl</a> operation, the <b>fName</b> member of this structure should be set to the name of the symbol's member to which this structure applies and the <b>fOptions</b> member should reflect the desired functionality of the operation.  The other members are either optional, or are filled in by <b>Ioctl</b>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>WdbgExts.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550906">IG_DUMP_SYMBOL_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551084">Ioctl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540429">DBG_DUMP_FIELD_XXX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553487">PSYM_DUMP_FIELD_CALLBACK</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20FIELD_INFO structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
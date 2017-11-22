---
UID: NS.mpiodisk._DsmSetLoadBalancePolicyALUA_IN
title: DsmSetLoadBalancePolicyALUA_IN
author: windows-driver-content
description: The DsmSetLoadBalancePolicyALUA_IN structure provides the input parameter for the DsmSetLoadBalancePolicyALUA method.
old-location: storage\dsmsetloadbalancepolicyalua_in.htm
ms.assetid: d46cfba0-a749-436a-99ad-d3606aea9a4d
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: mpiodisk.h
req.include-header: Mpiowmi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DsmSetLoadBalancePolicyALUA_IN
req.alt-loc: mpiodisk.h
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
ms.keywords: DsmSetLoadBalancePolicyALUA_IN, DsmSetLoadBalancePolicyALUA_IN, *PDsmSetLoadBalancePolicyALUA_IN
req.iface: 
---

# DsmSetLoadBalancePolicyALUA_IN structure



## -description
<p>The DsmSetLoadBalancePolicyALUA_IN structure provides the input parameter for the DsmSetLoadBalancePolicyALUA method.</p>


## -syntax

````
typedef struct _DsmSetLoadBalancePolicyALUA_IN {
  DSM_Load_Balance_Policy_V2 LoadBalancePolicy;
} DsmSetLoadBalancePolicyALUA_IN, *PDsmSetLoadBalancePolicyALUA_IN;
````


## -struct-fields
<dl>

### -field <b>LoadBalancePolicy</b>

<dd>
<p>A structure of type DSM_Load_Balance_Policy_V2.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Mpiodisk.h (include Mpiowmi.h)</dt>
</dl>
</td>
</tr>
</table>
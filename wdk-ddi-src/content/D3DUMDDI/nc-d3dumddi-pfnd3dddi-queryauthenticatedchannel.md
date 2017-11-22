---
UID: NC.d3dumddi.PFND3DDDI_QUERYAUTHENTICATEDCHANNEL
title: PFND3DDDI_QUERYAUTHENTICATEDCHANNEL
author: windows-driver-content
description: The QueryAuthenticatedChannel function queries an authenticated channel for capability and state information.
old-location: display\queryauthenticatedchannel.htm
ms.assetid: 13b65b5a-9512-4d67-b629-479bdd74674e
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: QueryAuthenticatedChannel is supported beginning with the Windows 7 operating system.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: QueryAuthenticatedChannel
req.alt-loc: d3dumddi.h
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
ms.keywords: DXGK_MIRACAST_CHUNK_INFO, DXGK_MIRACAST_CHUNK_INFO
req.iface: 
---

# PFND3DDDI_QUERYAUTHENTICATEDCHANNEL callback



## -description
<p>The <i>QueryAuthenticatedChannel</i> function queries an authenticated channel for capability and state information. </p>


## -prototype

````
PFND3DDDI_QUERYAUTHENTICATEDCHANNEL QueryAuthenticatedChannel;

__checkReturn HRESULT APIENTRY QueryAuthenticatedChannel(
  _In_          HANDLE                              hDevice,
  _Inout_ const D3DDDIARG_QUERYAUTHENTICATEDCHANNEL *pData
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to the display device (graphics context).</p>
</dd>

### -param <i>pData</i> [in, out]

<dd>
<p> A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543247">D3DDDIARG_QUERYAUTHENTICATEDCHANNEL</a> structure that describes authenticated-channel information to query. This structure contains an input buffer that describes the query and an output buffer to return the queried information. </p>
</dd>
</dl>

## -returns
<p><i>QueryAuthenticatedChannel</i> returns one of the following values:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The authenticated channel is successfully queried. </p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p><i>QueryAuthenticatedChannel</i> could not allocate the required memory for it to complete.</p>

<p> </p>

## -remarks
<p>The input buffer contains the driver's handle to the authenticated channel, a sequence number, and a GUID that indicates the type of query. The driver should fail all queries if the driver did not previously initialize the sequence number through a call to its <a href="https://msdn.microsoft.com/95485e96-fa4f-4c88-b88b-97b79f507abd">ConfigureAuthenticatedChannel</a> function. The driver should also fail the query if the sequence number is not greater than the sequence number of the previous query call. </p>

<p>The driver should duplicate the input data in the structure of the output buffer and should sign the output structure identically to how it currently handles <a href="https://msdn.microsoft.com/2c138dbd-55ca-4c71-8c8b-b2efd1ca80f2">Output Protection Manager</a> (OPM) queries.</p>

<p>Except for those situations in which the application incorrectly specifies an output buffer that is too small, the driver should always place the return code in the output structure. Therefore, the application has a secure mechanism to determine the return code. </p>

<p><i>QueryAuthenticatedChannel</i> performs different operations depending on each of following GUIDs that is specified in the input structure. The driver should fail if the input and output buffer sizes do not match the sizes that are defined for the specified GUID. </p>

<p></p><dl>
<dt><a id="D3DAUTHENTICATEDQUERY_PROTECTION"></a><a id="d3dauthenticatedquery_protection"></a>D3DAUTHENTICATEDQUERY_PROTECTION</dt>
<dd>
<p>The driver returns the current protection level for the device. This query can be used for both software and hardware channels, However, frequently polling the protection level is not required for a DDIAUTHENTICATEDCHANNEL_DRIVER_HARDWARE channel.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYPROTECTION_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_CHANNELTYPE"></a><a id="d3dauthenticatedquery_channeltype"></a>D3DAUTHENTICATEDQUERY_CHANNELTYPE</dt>
<dd>
<p>The driver returns the channel type. This query can be made for all channel types. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.  </p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCHANNELTYPE_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_DEVICEHANDLE"></a><a id="d3dauthenticatedquery_devicehandle"></a>D3DAUTHENTICATEDQUERY_DEVICEHANDLE</dt>
<dd>
<p>The driver returns a device identifier that the calling application can use to verify that multiple authenticated channels are indeed communicating with the same device. This query can be made for all channel types.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYDEVICEHANDLE_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_CRYPTOSESSION"></a><a id="d3dauthenticatedquery_cryptosession"></a>D3DAUTHENTICATEDQUERY_CRYPTOSESSION</dt>
<dd>
<p>The driver returns the crypto session handle (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) and the display device handle (the same handle that the driver's <i>QueryAuthenticatedChannel</i> function returned with the D3DAUTHENTICATEDQUERY_DEVICEHANDLE query) that are currently associated with the DirectX Video Acceleration (DirectX VA) decode device. The handle to the DirectX VA decode device is the same handle that the driver returned in response to the new DXVA2_DECODE_GET_DRIVER_HANDLE decode extension. For more information about DXVA2_DECODE_GET_DRIVER_HANDLE, see <a href="https://msdn.microsoft.com/2a3577f5-bc44-4e0d-a5fa-217dc6c6f5f3">Using Crypto Session with DirectX Video Accelerator 2.0 Decoder</a>.</p>
<p>This query can be made for all channel types.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCRYPTOSESSION_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYCRYPTOSESSION_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT"></a><a id="d3dauthenticatedquery_restrictedsharedresourceprocesscount"></a>D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT</dt>
<dd>
<p>While the operating system has a mechanism to restrict access to shared resources, the operating system protections are not robust against harmful code within the process or within the kernel. Therefore, this query exists to allow drivers to provide protections for extra level of robustness. Note that the driver cannot determine for sure which process is the Desktop Windows Manager (DWM) process; therefore, the driver must pick the most appropriate process. </p>
<p>These driver protections are only required for channel type DDIAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE because hardware protection can prevent resource data from being stolen more securely than these driver protections.</p>
<p>The driver returns the number of processes that are allowed to open the shared resources that were created with restricted access. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure. </p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERY RESTRICTEDSHAREDRESOURCEPROCESSCOUNT_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESS"></a><a id="d3dauthenticatedquery_restrictedsharedresourceprocess"></a>D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESS</dt>
<dd>
<p>The driver returns one of the processes that are allowed to open shared resources that were created with restricted access. The total number of these processes is returned with the D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT query. The DWM process is referenced by type rather than by process handle because applications cannot obtain a process handle for the DWM. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_UNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT"></a><a id="d3dauthenticatedquery_unresricttedprotectedsharedresourcecount"></a>D3DAUTHENTICATEDQUERY_UNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT</dt>
<dd>
<p>The driver returns the number of shared resources that were created as protected but are allowed to be opened by any process without restrictions. </p>
<p>This query can only be made for channel type D3DAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYUNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT"></a><a id="d3dauthenticatedquery_outputidcount"></a>D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT</dt>
<dd>
<p>The driver uses the OPM interface to enable protections on an individual output. However, OPM gives no assurance that the output that is controlled is the output that contains the protected content. </p>
<p>This query requests that the driver indicate the number of outputs on which the device presents its content. </p>
<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>
<p>The driver returns the number of output identifiers that is associated with the device and the crypto session. </p>
<p>This query can be made for all channel types. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_OUTPUTID"></a><a id="d3dauthenticatedquery_outputid"></a>D3DAUTHENTICATEDQUERY_OUTPUTID</dt>
<dd>
<p>This query requests the driver to return an identifier for each output on which the device presents its content. The number of these outputs is returned with the D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT query.</p>
<p>A new OPM query (DXGKMDT_OPM_GET_OUTPUT_ID) requests the driver to return the identifier for the output that the driver controls. The application can then ensure that the correct outputs are being managed.</p>
<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>
<p>This query can be made for all channel types.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTID_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYROUTPUTID_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_ACCESSIBILITYATTRIBUTES"></a><a id="d3dauthenticatedquery_accessibilityattributes"></a>D3DAUTHENTICATEDQUERY_ACCESSIBILITYATTRIBUTES</dt>
<dd></dd>
<dt><a id="D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUIDCOUNT"></a><a id="d3dauthenticatedquery_encryptionwhenaccessibleguidcount"></a>D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUIDCOUNT</dt>
<dd></dd>
<dt><a id="D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUID"></a><a id="d3dauthenticatedquery_encryptionwhenaccessibleguid"></a>D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUID</dt>
<dd></dd>
<dt><a id="D3DAUTHENTICATEDQUERY_CURRENTENCRYPTIONWHENACCESIBLE"></a><a id="d3dauthenticatedquery_currentencryptionwhenaccesible"></a>D3DAUTHENTICATEDQUERY_CURRENTENCRYPTIONWHENACCESIBLE</dt>
<dd></dd>
</dl><p>The driver returns the current protection level for the device. This query can be used for both software and hardware channels, However, frequently polling the protection level is not required for a DDIAUTHENTICATEDCHANNEL_DRIVER_HARDWARE channel.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYPROTECTION_OUTPUT structure. </p>

<p>The driver returns the channel type. This query can be made for all channel types. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.  </p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCHANNELTYPE_OUTPUT structure. </p>

<p>The driver returns a device identifier that the calling application can use to verify that multiple authenticated channels are indeed communicating with the same device. This query can be made for all channel types.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYDEVICEHANDLE_OUTPUT structure. </p>

<p>The driver returns the crypto session handle (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) and the display device handle (the same handle that the driver's <i>QueryAuthenticatedChannel</i> function returned with the D3DAUTHENTICATEDQUERY_DEVICEHANDLE query) that are currently associated with the DirectX Video Acceleration (DirectX VA) decode device. The handle to the DirectX VA decode device is the same handle that the driver returned in response to the new DXVA2_DECODE_GET_DRIVER_HANDLE decode extension. For more information about DXVA2_DECODE_GET_DRIVER_HANDLE, see <a href="https://msdn.microsoft.com/2a3577f5-bc44-4e0d-a5fa-217dc6c6f5f3">Using Crypto Session with DirectX Video Accelerator 2.0 Decoder</a>.</p>

<p>This query can be made for all channel types.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCRYPTOSESSION_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYCRYPTOSESSION_OUTPUT structure. </p>

<p>While the operating system has a mechanism to restrict access to shared resources, the operating system protections are not robust against harmful code within the process or within the kernel. Therefore, this query exists to allow drivers to provide protections for extra level of robustness. Note that the driver cannot determine for sure which process is the Desktop Windows Manager (DWM) process; therefore, the driver must pick the most appropriate process. </p>

<p>These driver protections are only required for channel type DDIAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE because hardware protection can prevent resource data from being stolen more securely than these driver protections.</p>

<p>The driver returns the number of processes that are allowed to open the shared resources that were created with restricted access. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure. </p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERY RESTRICTEDSHAREDRESOURCEPROCESSCOUNT_OUTPUT structure. </p>

<p>The driver returns one of the processes that are allowed to open shared resources that were created with restricted access. The total number of these processes is returned with the D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT query. The DWM process is referenced by type rather than by process handle because applications cannot obtain a process handle for the DWM. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_OUTPUT structure. </p>

<p>The driver returns the number of shared resources that were created as protected but are allowed to be opened by any process without restrictions. </p>

<p>This query can only be made for channel type D3DAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYUNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT_OUTPUT structure. </p>

<p>The driver uses the OPM interface to enable protections on an individual output. However, OPM gives no assurance that the output that is controlled is the output that contains the protected content. </p>

<p>This query requests that the driver indicate the number of outputs on which the device presents its content. </p>

<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>

<p>The driver returns the number of output identifiers that is associated with the device and the crypto session. </p>

<p>This query can be made for all channel types. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_OUTPUT structure. </p>

<p>This query requests the driver to return an identifier for each output on which the device presents its content. The number of these outputs is returned with the D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT query.</p>

<p>A new OPM query (DXGKMDT_OPM_GET_OUTPUT_ID) requests the driver to return the identifier for the output that the driver controls. The application can then ensure that the correct outputs are being managed.</p>

<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>

<p>This query can be made for all channel types.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTID_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYROUTPUTID_OUTPUT structure. </p>

<p>The input buffer contains the driver's handle to the authenticated channel, a sequence number, and a GUID that indicates the type of query. The driver should fail all queries if the driver did not previously initialize the sequence number through a call to its <a href="https://msdn.microsoft.com/95485e96-fa4f-4c88-b88b-97b79f507abd">ConfigureAuthenticatedChannel</a> function. The driver should also fail the query if the sequence number is not greater than the sequence number of the previous query call. </p>

<p>The driver should duplicate the input data in the structure of the output buffer and should sign the output structure identically to how it currently handles <a href="https://msdn.microsoft.com/2c138dbd-55ca-4c71-8c8b-b2efd1ca80f2">Output Protection Manager</a> (OPM) queries.</p>

<p>Except for those situations in which the application incorrectly specifies an output buffer that is too small, the driver should always place the return code in the output structure. Therefore, the application has a secure mechanism to determine the return code. </p>

<p><i>QueryAuthenticatedChannel</i> performs different operations depending on each of following GUIDs that is specified in the input structure. The driver should fail if the input and output buffer sizes do not match the sizes that are defined for the specified GUID. </p>

<p></p><dl>
<dt><a id="D3DAUTHENTICATEDQUERY_PROTECTION"></a><a id="d3dauthenticatedquery_protection"></a>D3DAUTHENTICATEDQUERY_PROTECTION</dt>
<dd>
<p>The driver returns the current protection level for the device. This query can be used for both software and hardware channels, However, frequently polling the protection level is not required for a DDIAUTHENTICATEDCHANNEL_DRIVER_HARDWARE channel.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYPROTECTION_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_CHANNELTYPE"></a><a id="d3dauthenticatedquery_channeltype"></a>D3DAUTHENTICATEDQUERY_CHANNELTYPE</dt>
<dd>
<p>The driver returns the channel type. This query can be made for all channel types. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.  </p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCHANNELTYPE_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_DEVICEHANDLE"></a><a id="d3dauthenticatedquery_devicehandle"></a>D3DAUTHENTICATEDQUERY_DEVICEHANDLE</dt>
<dd>
<p>The driver returns a device identifier that the calling application can use to verify that multiple authenticated channels are indeed communicating with the same device. This query can be made for all channel types.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYDEVICEHANDLE_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_CRYPTOSESSION"></a><a id="d3dauthenticatedquery_cryptosession"></a>D3DAUTHENTICATEDQUERY_CRYPTOSESSION</dt>
<dd>
<p>The driver returns the crypto session handle (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) and the display device handle (the same handle that the driver's <i>QueryAuthenticatedChannel</i> function returned with the D3DAUTHENTICATEDQUERY_DEVICEHANDLE query) that are currently associated with the DirectX Video Acceleration (DirectX VA) decode device. The handle to the DirectX VA decode device is the same handle that the driver returned in response to the new DXVA2_DECODE_GET_DRIVER_HANDLE decode extension. For more information about DXVA2_DECODE_GET_DRIVER_HANDLE, see <a href="https://msdn.microsoft.com/2a3577f5-bc44-4e0d-a5fa-217dc6c6f5f3">Using Crypto Session with DirectX Video Accelerator 2.0 Decoder</a>.</p>
<p>This query can be made for all channel types.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCRYPTOSESSION_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYCRYPTOSESSION_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT"></a><a id="d3dauthenticatedquery_restrictedsharedresourceprocesscount"></a>D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT</dt>
<dd>
<p>While the operating system has a mechanism to restrict access to shared resources, the operating system protections are not robust against harmful code within the process or within the kernel. Therefore, this query exists to allow drivers to provide protections for extra level of robustness. Note that the driver cannot determine for sure which process is the Desktop Windows Manager (DWM) process; therefore, the driver must pick the most appropriate process. </p>
<p>These driver protections are only required for channel type DDIAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE because hardware protection can prevent resource data from being stolen more securely than these driver protections.</p>
<p>The driver returns the number of processes that are allowed to open the shared resources that were created with restricted access. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure. </p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERY RESTRICTEDSHAREDRESOURCEPROCESSCOUNT_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESS"></a><a id="d3dauthenticatedquery_restrictedsharedresourceprocess"></a>D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESS</dt>
<dd>
<p>The driver returns one of the processes that are allowed to open shared resources that were created with restricted access. The total number of these processes is returned with the D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT query. The DWM process is referenced by type rather than by process handle because applications cannot obtain a process handle for the DWM. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_UNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT"></a><a id="d3dauthenticatedquery_unresricttedprotectedsharedresourcecount"></a>D3DAUTHENTICATEDQUERY_UNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT</dt>
<dd>
<p>The driver returns the number of shared resources that were created as protected but are allowed to be opened by any process without restrictions. </p>
<p>This query can only be made for channel type D3DAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYUNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT"></a><a id="d3dauthenticatedquery_outputidcount"></a>D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT</dt>
<dd>
<p>The driver uses the OPM interface to enable protections on an individual output. However, OPM gives no assurance that the output that is controlled is the output that contains the protected content. </p>
<p>This query requests that the driver indicate the number of outputs on which the device presents its content. </p>
<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>
<p>The driver returns the number of output identifiers that is associated with the device and the crypto session. </p>
<p>This query can be made for all channel types. </p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_OUTPUTID"></a><a id="d3dauthenticatedquery_outputid"></a>D3DAUTHENTICATEDQUERY_OUTPUTID</dt>
<dd>
<p>This query requests the driver to return an identifier for each output on which the device presents its content. The number of these outputs is returned with the D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT query.</p>
<p>A new OPM query (DXGKMDT_OPM_GET_OUTPUT_ID) requests the driver to return the identifier for the output that the driver controls. The application can then ensure that the correct outputs are being managed.</p>
<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>
<p>This query can be made for all channel types.</p>
<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTID_INPUT structure.</p>
<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYROUTPUTID_OUTPUT structure. </p>
</dd>
<dt><a id="D3DAUTHENTICATEDQUERY_ACCESSIBILITYATTRIBUTES"></a><a id="d3dauthenticatedquery_accessibilityattributes"></a>D3DAUTHENTICATEDQUERY_ACCESSIBILITYATTRIBUTES</dt>
<dd></dd>
<dt><a id="D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUIDCOUNT"></a><a id="d3dauthenticatedquery_encryptionwhenaccessibleguidcount"></a>D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUIDCOUNT</dt>
<dd></dd>
<dt><a id="D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUID"></a><a id="d3dauthenticatedquery_encryptionwhenaccessibleguid"></a>D3DAUTHENTICATEDQUERY_ENCRYPTIONWHENACCESSIBLEGUID</dt>
<dd></dd>
<dt><a id="D3DAUTHENTICATEDQUERY_CURRENTENCRYPTIONWHENACCESIBLE"></a><a id="d3dauthenticatedquery_currentencryptionwhenaccesible"></a>D3DAUTHENTICATEDQUERY_CURRENTENCRYPTIONWHENACCESIBLE</dt>
<dd></dd>
</dl><p>The driver returns the current protection level for the device. This query can be used for both software and hardware channels, However, frequently polling the protection level is not required for a DDIAUTHENTICATEDCHANNEL_DRIVER_HARDWARE channel.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYPROTECTION_OUTPUT structure. </p>

<p>The driver returns the channel type. This query can be made for all channel types. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.  </p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCHANNELTYPE_OUTPUT structure. </p>

<p>The driver returns a device identifier that the calling application can use to verify that multiple authenticated channels are indeed communicating with the same device. This query can be made for all channel types.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYDEVICEHANDLE_OUTPUT structure. </p>

<p>The driver returns the crypto session handle (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) and the display device handle (the same handle that the driver's <i>QueryAuthenticatedChannel</i> function returned with the D3DAUTHENTICATEDQUERY_DEVICEHANDLE query) that are currently associated with the DirectX Video Acceleration (DirectX VA) decode device. The handle to the DirectX VA decode device is the same handle that the driver returned in response to the new DXVA2_DECODE_GET_DRIVER_HANDLE decode extension. For more information about DXVA2_DECODE_GET_DRIVER_HANDLE, see <a href="https://msdn.microsoft.com/2a3577f5-bc44-4e0d-a5fa-217dc6c6f5f3">Using Crypto Session with DirectX Video Accelerator 2.0 Decoder</a>.</p>

<p>This query can be made for all channel types.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYCRYPTOSESSION_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYCRYPTOSESSION_OUTPUT structure. </p>

<p>While the operating system has a mechanism to restrict access to shared resources, the operating system protections are not robust against harmful code within the process or within the kernel. Therefore, this query exists to allow drivers to provide protections for extra level of robustness. Note that the driver cannot determine for sure which process is the Desktop Windows Manager (DWM) process; therefore, the driver must pick the most appropriate process. </p>

<p>These driver protections are only required for channel type DDIAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE because hardware protection can prevent resource data from being stolen more securely than these driver protections.</p>

<p>The driver returns the number of processes that are allowed to open the shared resources that were created with restricted access. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure. </p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERY RESTRICTEDSHAREDRESOURCEPROCESSCOUNT_OUTPUT structure. </p>

<p>The driver returns one of the processes that are allowed to open shared resources that were created with restricted access. The total number of these processes is returned with the D3DAUTHENTICATEDQUERY_RESTRICTEDSHAREDRESOURCEPROCESSCOUNT query. The DWM process is referenced by type rather than by process handle because applications cannot obtain a process handle for the DWM. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYRESTRICTEDSHAREDRESOURCEPROCESS_OUTPUT structure. </p>

<p>The driver returns the number of shared resources that were created as protected but are allowed to be opened by any process without restrictions. </p>

<p>This query can only be made for channel type D3DAUTHENTICATEDCHANNEL_DRIVER_SOFTWARE.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERY_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_ QUERYUNRESRICTTEDPROTECTEDSHAREDRESOURCECOUNT_OUTPUT structure. </p>

<p>The driver uses the OPM interface to enable protections on an individual output. However, OPM gives no assurance that the output that is controlled is the output that contains the protected content. </p>

<p>This query requests that the driver indicate the number of outputs on which the device presents its content. </p>

<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>

<p>The driver returns the number of output identifiers that is associated with the device and the crypto session. </p>

<p>This query can be made for all channel types. </p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTIDCOUNT_OUTPUT structure. </p>

<p>This query requests the driver to return an identifier for each output on which the device presents its content. The number of these outputs is returned with the D3DAUTHENTICATEDQUERY_OUTPUTIDCOUNT query.</p>

<p>A new OPM query (DXGKMDT_OPM_GET_OUTPUT_ID) requests the driver to return the identifier for the output that the driver controls. The application can then ensure that the correct outputs are being managed.</p>

<p>The driver should fail if the crypto session handle that is specified (the same handle that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451619">CreateCryptoSession</a> function returned in the <b>hCryptoSession</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542923">D3DDDIARG_CREATECRYPTOSESSION</a> structure) is associated with a different display device than the one that is specified. </p>

<p>This query can be made for all channel types.</p>

<p>The input buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYOUTPUTID_INPUT structure.</p>

<p>The output buffer points to a D3DAUTHENTICATEDCHANNEL_QUERYROUTPUTID_OUTPUT structure. </p>

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
<p>Version</p>
</th>
<td width="70%">
<p><i>QueryAuthenticatedChannel</i> is supported beginning with the Windows 7 operating system.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/95485e96-fa4f-4c88-b88b-97b79f507abd">ConfigureAuthenticatedChannel</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543247">D3DDDIARG_QUERYAUTHENTICATEDCHANNEL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_QUERYAUTHENTICATEDCHANNEL callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>
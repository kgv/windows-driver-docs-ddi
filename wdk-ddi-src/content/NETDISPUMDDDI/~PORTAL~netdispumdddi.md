# Declarations in the netdispumdddi header
This header Netdispumdddi contains these programming interfaces:

Callback

| Title        | Description    |
| ------------- |:-------------:|
| [PFN_REPORT_STATISTIC callback](nc-netdispumdddi-pfn-report-statistic.md) | Called by the user-mode display driver to report the statistics of the Miracast link to the operating system.The data type of this function is PFN_REPORT_STATISTIC. |
| [PFN_STOP_MIRACAST_SESSION callback](nc-netdispumdddi-pfn-stop-miracast-session.md) | Called by the operating system to start a Miracast connected session that had earlier been started by a call to the StartMiracastSession function. |
| [PFN_REGISTER_DATARATE_NOTIFICATIONS callback](nc-netdispumdddi-pfn-register-datarate-notifications.md) | Called by the user-mode driver to register with the operating system to receive network quality of service (QoS) notifications and the current network bandwidth of the Miracast connection.The data type of this function is PFN_REGISTER_DATARATE_NOTIFICATIONS. |
| [PFN_REPORT_SESSION_STATUS callback](nc-netdispumdddi-pfn-report-session-status.md) | Called by the user-mode display driver to report the status of the current Miracast connected session.The data type of this function is PFN_REPORT_SESSION_STATUS. |
| [PFN_DATARATE_NOTIFICATION callback](nc-netdispumdddi-pfn-datarate-notification.md) | Called by the operating system to notify the Miracast user-mode driver that the bit rate of the Miracast network link has changed. This function is registered with the operating system when the RegisterForDataRateNotifications function is called. |
| [QUERY_MIRACAST_DRIVER_INTERFACE callback](nc-netdispumdddi-query-miracast-driver-interface.md) | Called by the operating system to query the Miracast user-mode driver interface, MIRACAST_DRIVER_INTERFACE. |
| [PFN_DESTROY_MIRACAST_CONTEXT callback](nc-netdispumdddi-pfn-destroy-miracast-context.md) | Called by the operating system to destroy a user-mode Miracast context. |
| [PFN_CREATE_MIRACAST_CONTEXT callback](nc-netdispumdddi-pfn-create-miracast-context.md) | Called by the operating system to create a user-mode Miracast context. |
| [PFN_MIRACAST_IO_CONTROL callback](nc-netdispumdddi-pfn-miracast-io-control.md) | Called by the user-mode display driver to send the kernel-mode display miniport driver a synchronous I/O control request.The data type of this function is PFN_MIRACAST_IO_CONTROL. |
| [PFN_START_MIRACAST_SESSION callback](nc-netdispumdddi-pfn-start-miracast-session.md) | Called by the operating system to start a Miracast connected session. |
| [PFN_GET_NEXT_CHUNK_DATA callback](nc-netdispumdddi-pfn-get-next-chunk-data.md) | Provides info about the next Miracast encode chunk that was reported to the Microsoft DirectX graphics kernel subsystem when the DXGK_INTERRUPT_TYPE interrupt type is DXGK_INTERRUPT_MICACAST_CHUNK_PROCESSING_COMPLETE.The data type of this function is PFN_GET_NEXT_CHUNK_DATA. |
| [PFN_HANDLE_KMD_MESSAGE callback](nc-netdispumdddi-pfn-handle-kmd-message.md) | Called by the operating system to handle the asynchronous kernel-mode message that the Miracast user-mode driver receives when the display miniport driver calls the DxgkCbMiracastSendMessage function. |
Enum

| Title        | Description    |
| ------------- |:-------------:|
| [MIRACAST_PROTOCOL_EVENT enumeration](ne-netdispumdddi-miracast-protocol-event.md) | Specifies the types of wireless display (Miracast) protocol event that the user-mode display driver should report. |
| [MIRACAST_STATUS enumeration](ne-netdispumdddi-miracast-status.md) | Specifies status types that the user-mode display driver uses to report Miracast connection status. |
| [MIRACAST_CHUNK_TYPE enumeration](ne-netdispumdddi-miracast-chunk-type.md) | Specifies the types of wireless display (Miracast) chunk info that is to be processed. |
| [MIRACAST_STATISTIC_TYPE enumeration](ne-netdispumdddi-miracast-statistic-type.md) | Specifies types of Miracast statistics data that the user-mode display driver generates. |
Struct

| Title        | Description    |
| ------------- |:-------------:|
| [MIRACAST_CALLBACKS structure](ns-netdispumdddi--miracast-callbacks.md) | Contains pointers to wireless display (Miracast) runtime callback functions that the Miracast user-mode driver can call. |
| [MIRACAST_CHUNK_INFO structure](ns-netdispumdddi-miracast-chunk-info.md) | Contains info about a specified wireless display (Miracast) encode chunk. |
| [MIRACAST_DATARATE_STATS structure](ns-netdispumdddi-miracast-datarate-stats.md) | Contains info used in the wireless display (Miracast) pfnDataRateNotify function about the audio/video encoder bit rate and failed or retried Wi-Fi frames. |
| [MIRACAST_DRIVER_INTERFACE structure](ns-netdispumdddi--miracast-driver-interface.md) | Contains pointers to wireless display (Miracast) functions that are implemented by the Miracast user-mode driver. |
| [MIRACAST_WFD_CONNECTION_STATS structure](ns-netdispumdddi-miracast-wfd-connection-stats.md) | Contains bit rate info on the Wi-Fi Direct connection. |
| [MIRACAST_STATISTIC_DATA structure](ns-netdispumdddi-miracast-statistic-data.md) | Contains Miracast statistics data that the user-mode display driver reports to the operating system. |
| [MIRACAST_SESSION_INFO structure](ns-netdispumdddi-miracast-session-info.md) | Contains info on a wireless display (Miracast) connected session. |
| [MIRACAST_CHUNK_DATA structure](ns-netdispumdddi-miracast-chunk-data.md) | Contains encode chunk data that is used when a user-mode driver calls the wireless display (Miracast) GetNextChunkData function. |
| [MIRACAST_CHUNK_ID structure](ns-netdispumdddi-miracast-chunk-id.md) | Stores info that identifies a wireless display (Miracast) encode chunk. |

This header is used in these topics:

- [display](..content/_display)
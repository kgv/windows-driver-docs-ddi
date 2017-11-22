# Declarations in the ucxcontroller header
This header Ucxcontroller contains these programming interfaces:

Function

| Title        | Description    |
| ------------- |:-------------:|
| [UcxIoDeviceControl function](nf-ucxcontroller-ucxiodevicecontrol.md) | TBD |
| [UCX_CONTROLLER_RESET_COMPLETE_INFO_INIT function](nf-ucxcontroller-ucx-controller-reset-complete-info-init.md) | TBD |
| [UcxControllerSetIdStrings function](nf-ucxcontroller-ucxcontrollersetidstrings.md) | Updates the identifier strings of a controller after the controller has been initialized. |
| [UCX_CONTROLLER_CONFIG_SET_ACPI_INFO function](nf-ucxcontroller-ucx-controller-config-set-acpi-info.md) | Initializes a UCX_CONTROLLER_CONFIG structure with the specified values for the controller with ACPI as the parent. |
| [UcxControllerNotifyTransportCharacteristicsChange function](nf-ucxcontroller-ucxcontrollernotifytransportcharacteristicschange.md) | Notifies UCX about a new port change event from host controller. |
| [UcxControllerNeedsReset function](nf-ucxcontroller-ucxcontrollerneedsreset.md) | TBD |
| [UCX_CONTROLLER_CONFIG_SET_PCI_INFO function](nf-ucxcontroller-ucx-controller-config-set-pci-info.md) | Initializes a UCX_CONTROLLER_CONFIG structure with the specified values for the controller with PCI as the parent bus type. |
| [UcxControllerResetComplete function](nf-ucxcontroller-ucxcontrollerresetcomplete.md) | TBD |
| [UcxControllerSetFailed function](nf-ucxcontroller-ucxcontrollersetfailed.md) | TBD |
Callback

| Title        | Description    |
| ------------- |:-------------:|
| [EVT_UCX_CONTROLLER_GET_FRAME_NUMBER_AND_QPC_FOR_TIME_SYNC callback](nc-ucxcontroller-evt-ucx-controller-get-frame-number-and-qpc-for-time-sync.md) | UCX invokes this callback to retrieves the system query performance counter (QPC) value synchronized with the frame and microframe. |
| [EVT_UCX_CONTROLLER_RESET callback](nc-ucxcontroller-evt-ucx-controller-reset.md) | The client driver's implementation that UCX calls to reset the controller. |
| [PFN_UCXCONTROLLERRESETCOMPLETE callback function](nc-ucxcontroller-pfn-ucxcontrollerresetcomplete.md) | TBD |
| [PFN_UCXCONTROLLERNOTIFYTRANSPORTCHARACTERISTICSCHANGE callback function](nc-ucxcontroller-pfn-ucxcontrollernotifytransportcharacteristicschange.md) | TBD |
| [EVT_UCX_CONTROLLER_GET_TRANSPORT_CHARACTERISTICS callback](nc-ucxcontroller-evt-ucx-controller-get-transport-characteristics.md) | UCX invokes this callback to retrieve the host controller characteristics. |
| [EVT_UCX_CONTROLLER_QUERY_USB_CAPABILITY callback](nc-ucxcontroller-evt-ucx-controller-query-usb-capability.md) | The client driver's implementation to determine if the controller supports a specific capability. |
| [EVT_UCX_CONTROLLER_START_TRACKING_FOR_TIME_SYNC callback](nc-ucxcontroller-evt-ucx-controller-start-tracking-for-time-sync.md) | UCX invokes this callback function to the start time tracking functionality in the controller. |
| [EVT_UCX_CONTROLLER_SET_TRANSPORT_CHARACTERISTICS_CHANGE_NOTIFICATION callback](nc-ucxcontroller-evt-ucx-controller-set-transport-characteristics-change-notification.md) | UCX invokes this callback function to specify its preference in transport characteristics for which the client driver must send notifications when changes occur. |
| [PFN_UCXIODEVICECONTROL callback function](nc-ucxcontroller-pfn-ucxiodevicecontrol.md) | TBD |
| [EVT_UCX_CONTROLLER_GET_CURRENT_FRAMENUMBER callback](nc-ucxcontroller-evt-ucx-controller-get-current-framenumber.md) | The client driver's implementation that UCX calls to retrieve the current 32-bit frame number. |
| [PFN_UCXCONTROLLERSETFAILED callback function](nc-ucxcontroller-pfn-ucxcontrollersetfailed.md) | TBD |
| [EVT_UCX_CONTROLLER_STOP_TRACKING_FOR_TIME_SYNC callback](nc-ucxcontroller-evt-ucx-controller-stop-tracking-for-time-sync.md) | UCX invokes this callback function to the stop time tracking functionality in the controller. |
| [PFN_UCXCONTROLLERSETIDSTRINGS callback function](nc-ucxcontroller-pfn-ucxcontrollersetidstrings.md) | TBD |
| [PFN_UCXCONTROLLERNEEDSRESET callback function](nc-ucxcontroller-pfn-ucxcontrollerneedsreset.md) | TBD |
| [EVT_UCX_CONTROLLER_USBDEVICE_ADD callback](nc-ucxcontroller-evt-ucx-controller-usbdevice-add.md) | The client driver's implementation that UCX calls when a new USB device is detected. |
Enum

| Title        | Description    |
| ------------- |:-------------:|
| [UCX_CONTROLLER_STATE enumeration](ne-ucxcontroller--ucx-controller-state.md) | This enumeration provides values to specify the UCX controller state after a reset. |
| [UCX_CONTROLLER_PARENT_BUS_TYPE enumeration](ne-ucxcontroller--ucx-controller-parent-bus-type.md) | The UCX_CONTROLLER_PARENT_BUS_TYPE enumeration defines the parent bus type. |
Struct

| Title        | Description    |
| ------------- |:-------------:|
| [UCX_CONTROLLER_TRANSPORT_CHARACTERISTICS structure](ns-ucxcontroller--ucx-controller-transport-characteristics.md) | Stores the transport characteristics at relevant points in time. This structure is used in the EVT_UCX_CONTROLLER_GET_TRANSPORT_CHARACTERISTICS callback function. |
| [UCX_CONTROLLER_RESET_COMPLETE_INFO structure](ns-ucxcontroller--ucx-controller-reset-complete-info.md) | Contains information about the operation to reset the controller. This is used by the client driver in its EVT_UCX_CONTROLLER_RESET callback function. |
| [UCXUSBDEVICE_INFO structure](ns-ucxcontroller--ucxusbdevice-info.md) | TBD |
| [UCX_CONTROLLER_TRANSPORT_CHARACTERISTICS_CHANGE_FLAGS structure](ns-ucxcontroller--ucx-controller-transport-characteristics-change-flags.md) | Defines flags for the transport characteristics changes. This structure is used in the EVT_UCX_CONTROLLER_SET_TRANSPORT_CHARACTERISTICS_CHANGE_NOTIFICATION callback function. |
| [UCX_CONTROLLER_ACPI_INFORMATION structure](ns-ucxcontroller--ucx-controller-acpi-information.md) | This structure provides information about an advanced Configuration and power interface (ACPI) USB controller. |
| [UCX_CONTROLLER_CONFIG structure](ns-ucxcontroller--ucx-controller-config.md) | This structure configuration data for a USB controller. |
| [UCX_CONTROLLER_PCI_INFORMATION structure](ns-ucxcontroller--ucx-controller-pci-information.md) | This structure provides information about a PCI USB controller. |

This header is used in these topics:

- [usbref](..content/_usbref)
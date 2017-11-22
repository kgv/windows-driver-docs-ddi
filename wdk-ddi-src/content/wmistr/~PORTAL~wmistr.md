# Declarations in the wmistr header
This header Wmistr contains these programming interfaces:

Struct

| Title        | Description    |
| ------------- |:-------------:|
| [tagWNODE_ALL_DATA structure](ns-wmistr-tagwnode-all-data.md) | The WNODE_ALL_DATA structure contains data for all instances of a data block or event block. |
| [tagWNODE_TOO_SMALL structure](ns-wmistr-tagwnode-too-small.md) | The WNODE_TOO_SMALL structure indicates the size of the buffer needed to receive output from a request. |
| [tagWNODE_EVENT_ITEM structure](ns-wmistr-tagwnode-event-item.md) | The WNODE_EVENT_ITEM structure contains data generated by a driver for an event. |
| [tagWNODE_METHOD_ITEM structure](ns-wmistr-tagwnode-method-item.md) | The WNODE_METHOD_ITEM structure indicates a method associated with an instance of a data block and contains any input data for the method. |
| [tagWNODE_SINGLE_INSTANCE structure](ns-wmistr-tagwnode-single-instance.md) | The WNODE_SINGLE_INSTANCE structure contains values for all data items in one instance of a data block. |
| [tagWNODE_EVENT_REFERENCE structure](ns-wmistr-tagwnode-event-reference.md) | The WNODE_EVENT_REFERENCE structure contains information that WMI can use to query for an event that exceeds the event size limit set in the registry. |
| [POFFSETINSTANCEDATAANDLENGTH structure](ns-wmistr-poffsetinstancedataandlength.md) | TBD |
| [tagWNODE_SINGLE_ITEM structure](ns-wmistr-tagwnode-single-item.md) | The WNODE_SINGLE_ITEM structure contains the value of a single data item in an instance of a data block. |
| [PWMIREGGUIDW structure](ns-wmistr-pwmiregguidw.md) | TBD |
| [PWMIREGINFOW structure](ns-wmistr-pwmireginfow.md) | TBD |
| [WNODE_HEADER structure](ns-wmistr--wnode-header.md) | The WNODE_HEADER structure is the first member of all other WNODE_XXX structures. It contains information common to all such structures. |
Enum

| Title        | Description    |
| ------------- |:-------------:|
| [WMIDPREQUESTCODE enumeration](ne-wmistr-wmidprequestcode.md) | TBD |

This header is used in these topics:

- [kernel](..content/_kernel)
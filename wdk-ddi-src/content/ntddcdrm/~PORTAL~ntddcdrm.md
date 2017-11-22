# Declarations in the ntddcdrm header
This header Ntddcdrm contains these programming interfaces:

Enum

| Title        | Description    |
| ------------- |:-------------:|
| [CDROM_PERFORMANCE_REQUEST_TYPE enumeration](ne-ntddcdrm--cdrom-performance-request-type.md) | The CDROM_PERFORMANCE_REQUEST_TYPE enumeration defines the types of performance data requests. It is a member of the CDROM_PERFORMANCE_REQUEST structure, which is used as an input parameter to the IOCTL_CDROM_GET_PERFORMANCE I/O control request. |
| [EXCLUSIVE_ACCESS_REQUEST_TYPE enumeration](ne-ntddcdrm--exclusive-access-request-type.md) | The EXCLUSIVE_ACCESS_REQUEST_TYPE enumeration is used to report the exclusive access state of a CD-ROM device. |
| [CDROM_PERFORMANCE_TOLERANCE_TYPE enumeration](ne-ntddcdrm--cdrom-performance-tolerance-type.md) | The CDROM_PERFORMANCE_TOLERANCE_TYPE enumeration defines the allowable tolerances for performance data. It is a member of the CDROM_PERFORMANCE_REQUEST structure, which is used as an input parameter to the IOCTL_CDROM_GET_PERFORMANCE I/O control request. |
| [TRACK_MODE_TYPE enumeration](ne-ntddcdrm--track-mode-type.md) | The TRACK_MODE_TYPE enumeration type is used in conjunction with the IOCTL_CDROM_RAW_READ request and the RAW_READ_INFO structure to read data from a CD-ROM in raw mode. |
| [CDROM_OPC_INFO_TYPE enumeration](ne-ntddcdrm--cdrom-opc-info-type.md) | The CDROM_OPC_INFO_TYPE enumeration is a member of the CDROM_SIMPLE_OPC_INFO structure. It defines the Optimum Power Calibration (OPC) request that is used as input to the IOCTL_CDROM_SEND_OPC_INFORMATION I/O control request. |
| [CDROM_PERFORMANCE_EXCEPTION_TYPE enumeration](ne-ntddcdrm--cdrom-performance-exception-type.md) | The CDROM_PERFORMANCE_EXCEPTION_TYPE enumeration defines the exceptional conditions for performance data. |
| [MEDIA_BLANK_TYPE enumeration](ne-ntddcdrm--media-blank-type.md) | TBD |
| [CDROM_PERFORMANCE_TYPE enumeration](ne-ntddcdrm--cdrom-performance-type.md) | The CDROM_PERFORMANCE_TYPE enumeration defines the read and write performance data requests. It is a member of the CDROM_PERFORMANCE_REQUEST structure, which is used as an input parameter to the IOCTL_CDROM_GET_PERFORMANCE I/O control request. |
| [CDROM_SPEED_REQUEST enumeration](ne-ntddcdrm--cdrom-speed-request.md) | The CDROM_SPEED_REQUEST enumeration indicates which command that the CD-ROM class driver will use to set the spindle speed of a CD-ROM drive. |
| [STREAMING_CONTROL_REQUEST_TYPE enumeration](ne-ntddcdrm--streaming-control-request-type.md) | The STREAMING_CONTROL_REQUEST_TYPE enumeration defines the CDROM streaming modes. |
| [WRITE_ROTATION enumeration](ne-ntddcdrm--write-rotation.md) | The WRITE_ROTATION enumeration specifies whether a CD-ROM drive uses constant linear velocity (CLV) rotation or constant angular velocity (CAV) rotation when it writes to a CD. |
Struct

| Title        | Description    |
| ------------- |:-------------:|
| [RAW_READ_INFO structure](ns-ntddcdrm---raw-read-info.md) | The RAW_READ_INFO structure is used in conjunction with the IOCTL_CDROM_RAW_READ request to read data from a CD-ROM in raw mode. |
| [CDROM_WRITE_SPEED_DESCRIPTOR structure](ns-ntddcdrm--cdrom-write-speed-descriptor.md) | The CDROM_WRITE_SPEED_DESCRIPTOR structure is returned for the IOCTL_CDROM_GET_PERFORMANCE IOCTL when the request type is CdromWriteSpeedRequest. |
| [CDROM_SIMPLE_OPC_INFO structure](ns-ntddcdrm--cdrom-simple-opc-info.md) | The CDROM_SIMPLE_OPC_INFO structure is the only input for the IOCTL_CDROM_SEND_OPC_INFORMATION I/O control code. |
| [TRACK_DATA structure](ns-ntddcdrm--track-data.md) | Track descriptor is used in conjunction with CDROM_TOC and CDROM_TOC_SESSION_DATA. |
| [CDROM_SET_SPEED structure](ns-ntddcdrm--cdrom-set-speed.md) | The CDROM_SET_SPEED structure is used with the IOCTL_CDROM_SET_SPEED request to set the spindle speed of a CD-ROM drive during data transfers in which no data loss is permitted. |
| [SUB_Q_HEADER structure](ns-ntddcdrm--sub-q-header.md) | The SUB_Q_HEADER structure contains audio status information and the length of the Q subchannel data being returned. This structure is used in conjunction with SUB_Q_CHANNEL_DATA. |
| [CDROM_SET_STREAMING structure](ns-ntddcdrm--cdrom-set-streaming.md) | The CDROM_SET_SPEED structure is used with the IOCTL_CDROM_SET_SPEED request to set the spindle speed of a CD-ROM drive during isochronous transfers that permit some data loss. |
| [CDROM_WRITE_SPEED_REQUEST structure](ns-ntddcdrm--cdrom-write-speed-request.md) | The CDROM_WRITE_SPEED_REQUEST structure is used as an input parameter to the IOCTL_CDROM_GET_PERFORMANCE IOCTL and for requesting write speed descriptors. |
| [CDROM_EXCEPTION_PERFORMANCE_DESCRIPTOR structure](ns-ntddcdrm--cdrom-exception-performance-descriptor.md) | The CDROM_EXCEPTION_PERFORMANCE_DESCRIPTOR structure indicates that the result data from the IOCTL_CDROM_GET_PERFORMANCE I/O control request is for exception conditions. |
| [CDROM_STREAMING_CONTROL structure](ns-ntddcdrm--cdrom-streaming-control.md) | The CDROM_STREAMING_CONTROL structure is used as an input parameter to the IOCTL_CDROM_ENABLE_STREAMING IOCTL. |
| [CDROM_EXCLUSIVE_LOCK_STATE structure](ns-ntddcdrm--cdrom-exclusive-lock-state.md) | The CDROM_EXCLUSIVE_LOCK_STATE structure is used by the CD-ROM class driver to report the exclusive access state of a CD-ROM device. |
| [CDROM_TOC_CD_TEXT_DATA_BLOCK structure](ns-ntddcdrm--cdrom-toc-cd-text-data-block.md) | This structure contains CD text descriptor data used in conjunction with the data in the CDROM_TOC_CD_TEXT_DATA structure. |
| [CDROM_SEEK_AUDIO_MSF structure](ns-ntddcdrm--cdrom-seek-audio-msf.md) | The CDROM_SEEK_AUDIO_MSF structure contains the minute, second, and frame that the device must seek to upon receipt of a device control IRP with a control code of IOCTL_CDROM_SEEK_AUDIO_MSF. |
| [SUB_Q_TRACK_ISRC structure](ns-ntddcdrm--sub-q-track-isrc.md) | The SUB_Q_TRACK_ISC contains position information and is used in conjunction with the SUB_Q_CHANNEL_DATA structure. |
| [CDROM_EXCLUSIVE_LOCK structure](ns-ntddcdrm--cdrom-exclusive-lock.md) | The CDROM_EXCLUSIVE_LOCK structure is used with the IOCTL_CDROM_EXCLUSIVE_ACCESS request to lock a CD-ROM device for exclusive access. |
| [CDROM_PLAY_AUDIO_MSF structure](ns-ntddcdrm--cdrom-play-audio-msf.md) | Device control IRPs with a control code of IOCTL_CDROM_PLAY_AUDIO_MSF use this structure to play an audio CD. |
| [CDROM_TOC_CD_TEXT_DATA structure](ns-ntddcdrm--cdrom-toc-cd-text-data.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_CDTEXT return their output data in this structure followed by a series of descriptors of type CDROM_TOC_CD_TEXT_DATA_BLOCK. |
| [CDROM_TOC_FULL_TOC_DATA structure](ns-ntddcdrm--cdrom-toc-full-toc-data.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_FULL_TOC return their output data in this structure optionally followed by a series of descriptors of type CDROM_TOC_FULL_TOC_DATA_BLOCK. |
| [SUB_Q_CHANNEL_DATA structure](ns-ntddcdrm--sub-q-channel-data.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_Q_CHANNEL return their output data in this union. |
| [CDROM_TOC_ATIP_DATA_BLOCK structure](ns-ntddcdrm--cdrom-toc-atip-data-block.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_ATIP return their output data in a header structure of type CDROM_TOC_ATIP_DATA followed by a series of ATIP data block descriptors defined by CDROM_TOC_ATIP_DATA_BLOCK. |
| [CDROM_EXCLUSIVE_ACCESS structure](ns-ntddcdrm--cdrom-exclusive-access.md) | The CDROM_EXCLUSIVE_ACCESS structure is used with the IOCTL_CDROM_EXCLUSIVE_ACCESS request to query the access state of a CD-ROM device or to lock or unlock the device for exclusive access. |
| [CDROM_PERFORMANCE_HEADER structure](ns-ntddcdrm--cdrom-performance-header.md) | The CDROM_PERFORMANCE_HEADER structure is used by the IOCTL_CDROM_GET_PERFORMANCE IOCTL to return data. When the request type is CdromPerformanceRequest, the IOCTL returns this header followed by optional descriptors. |
| [VOLUME_CONTROL structure](ns-ntddcdrm--volume-control.md) | The VOLUME_CONTROL structure is used in conjunction with the IOCTL_CDROM_GET_VOLUME request to retrieve volume values for up to four audio ports. |
| [CDROM_AUDIO_CONTROL structure](ns-ntddcdrm--cdrom-audio-control.md) | The CDROM_AUDIO_CONTROL structure is used in conjunction with the IOCTL_CDROM_GET_CONTROL request to report the audio playback mode. |
| [SUB_Q_MEDIA_CATALOG_NUMBER structure](ns-ntddcdrm--sub-q-media-catalog-number.md) | The SUB_Q_MEDIA_CATALOG_NUMBER structure contains position information and is used in conjunction with the SUB_Q_CHANNEL_DATA structure. |
| [CDROM_PERFORMANCE_REQUEST structure](ns-ntddcdrm--cdrom-performance-request.md) | The CDROM_PERFORMANCE_REQUEST structure is used as an input parameter to the IOCTL_CDROM_GET_PERFORMANCE I/O control request and describes the performance data requested. |
| [CDROM_TOC_FULL_TOC_DATA_BLOCK structure](ns-ntddcdrm--cdrom-toc-full-toc-data-block.md) | The CDROM_TOC_FULL_TOC_DATA_BLOCK structure contains track descriptor data used in conjunction with the data from the CDROM_TOC_FULL_TOC_DATA structure. |
| [SUB_Q_CURRENT_POSITION structure](ns-ntddcdrm--sub-q-current-position.md) | The SUB_Q_CURRENT_POSITION structure contains position information and is used in conjunction with SUB_Q_CHANNEL_DATA. |
| [CDROM_READ_TOC_EX structure](ns-ntddcdrm--cdrom-read-toc-ex.md) | When drivers query a target CD-ROM device with IOCTL_CDROM_READ_TOC_EX they must define the query with this structure. |
| [CDROM_DISK_DATA structure](ns-ntddcdrm--cdrom-disk-data.md) | TBD |
| [CDROM_SUB_Q_DATA_FORMAT structure](ns-ntddcdrm--cdrom-sub-q-data-format.md) | The CDROM_SUB_Q_DATA_FORMAT structure is used with device control IRPs of type IOCTL_CDROM_READ_Q_CHANNEL. |
| [CDROM_TOC_SESSION_DATA structure](ns-ntddcdrm--cdrom-toc-session-data.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_SESSION return their output data in this structure followed by a series of TRACK_DATA structures. |
| [CDROM_TOC_PMA_DATA structure](ns-ntddcdrm--cdrom-toc-pma-data.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_PMA return their output data in this structure optionally followed by a series of descriptors of type CDROM_TOC_FULL_TOC_DATA_BLOCK. |
| [CDROM_TOC structure](ns-ntddcdrm--cdrom-toc.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_TOC return their output data in this structure followed by a series of TRACK_DATA structures. |
| [CDROM_NOMINAL_PERFORMANCE_DESCRIPTOR structure](ns-ntddcdrm--cdrom-nominal-performance-descriptor.md) | The CDROM_NOMINAL_PERFORMANCE_DESCRIPTOR structure gives the host an approximation of logical unit performance. |
| [CDROM_TOC_ATIP_DATA structure](ns-ntddcdrm--cdrom-toc-atip-data.md) | Device control IRPs with a control code of IOCTL_CDROM_READ_TOC_EX and a format of CDROM_READ_TOC_EX_FORMAT_ATIP return their output data in this header structure followed by a series of descriptors of type CDROM_TOC_ATIP_DATA_BLOCK. |
Ioctl

| Title        | Description    |
| ------------- |:-------------:|
| [IOCTL_CDROM_SEEK_AUDIO_MSF IOCTL](ni-ntddcdrm-ioctl-cdrom-seek-audio-msf.md) | TBD |
| [IOCTL_CDROM_GET_CONTROL IOCTL](ni-ntddcdrm-ioctl-cdrom-get-control.md) | TBD |
| [IOCTL_CDROM_READ_Q_CHANNEL IOCTL](ni-ntddcdrm-ioctl-cdrom-read-q-channel.md) | TBD |
| [IOCTL_CDROM_READ_TOC_EX IOCTL](ni-ntddcdrm-ioctl-cdrom-read-toc-ex.md) | TBD |
| [IOCTL_CDROM_MEDIA_CATALOG IOCTL](ni-ntddcdrm-ioctl-cdrom-media-catalog.md) | TBD |
| [IOCTL_CDROM_RELEASE IOCTL](ni-ntddcdrm-ioctl-cdrom-release.md) | TBD |
| [IOCTL_CDROM_BASE IOCTL](ni-ntddcdrm-ioctl-cdrom-base.md) | TBD |
| [IOCTL_CDROM_DISK_TYPE IOCTL](ni-ntddcdrm-ioctl-cdrom-disk-type.md) | TBD |
| [IOCTL_CDROM_RESERVE IOCTL](ni-ntddcdrm-ioctl-cdrom-reserve.md) | TBD |
| [IOCTL_CDROM_MEDIA_REMOVAL IOCTL](ni-ntddcdrm-ioctl-cdrom-media-removal.md) | TBD |
| [IOCTL_CDROM_FIND_NEW_DEVICES IOCTL](ni-ntddcdrm-ioctl-cdrom-find-new-devices.md) | TBD |
| [IOCTL_CDROM_PAUSE_AUDIO IOCTL](ni-ntddcdrm-ioctl-cdrom-pause-audio.md) | TBD |
| [IOCTL_CDROM_EXCLUSIVE_ACCESS IOCTL](ni-ntddcdrm-ioctl-cdrom-exclusive-access.md) | TBD |
| [IOCTL_CDROM_LOAD_MEDIA IOCTL](ni-ntddcdrm-ioctl-cdrom-load-media.md) | TBD |
| [IOCTL_CDROM_SET_SPEED IOCTL](ni-ntddcdrm-ioctl-cdrom-set-speed.md) | TBD |
| [IOCTL_CDROM_SEND_OPC_INFORMATION IOCTL](ni-ntddcdrm-ioctl-cdrom-send-opc-information.md) | TBD |
| [IOCTL_CDROM_PLAY_AUDIO_MSF IOCTL](ni-ntddcdrm-ioctl-cdrom-play-audio-msf.md) | TBD |
| [IOCTL_CDROM_CURRENT_POSITION IOCTL](ni-ntddcdrm-ioctl-cdrom-current-position.md) | TBD |
| [IOCTL_CDROM_SUB_Q_CHANNEL IOCTL](ni-ntddcdrm-ioctl-cdrom-sub-q-channel.md) | TBD |
| [IOCTL_CDROM_GET_PERFORMANCE IOCTL](ni-ntddcdrm-ioctl-cdrom-get-performance.md) | TBD |
| [IOCTL_CDROM_GET_LAST_SESSION IOCTL](ni-ntddcdrm-ioctl-cdrom-get-last-session.md) | TBD |
| [IOCTL_CDROM_EJECT_MEDIA IOCTL](ni-ntddcdrm-ioctl-cdrom-eject-media.md) | TBD |
| [IOCTL_CDROM_SIMBAD IOCTL](ni-ntddcdrm-ioctl-cdrom-simbad.md) | TBD |
| [IOCTL_CDROM_UNLOAD_DRIVER IOCTL](ni-ntddcdrm-ioctl-cdrom-unload-driver.md) | TBD |
| [IOCTL_CDROM_TRACK_ISRC IOCTL](ni-ntddcdrm-ioctl-cdrom-track-isrc.md) | TBD |
| [IOCTL_CDROM_GET_INQUIRY_DATA IOCTL](ni-ntddcdrm-ioctl-cdrom-get-inquiry-data.md) | TBD |
| [IOCTL_CDROM_ENABLE_STREAMING IOCTL](ni-ntddcdrm-ioctl-cdrom-enable-streaming.md) | TBD |
| [IOCTL_CDROM_GET_DRIVE_GEOMETRY_EX IOCTL](ni-ntddcdrm-ioctl-cdrom-get-drive-geometry-ex.md) | TBD |
| [IOCTL_CDROM_GET_VOLUME IOCTL](ni-ntddcdrm-ioctl-cdrom-get-volume.md) | TBD |
| [IOCTL_CDROM_RESUME_AUDIO IOCTL](ni-ntddcdrm-ioctl-cdrom-resume-audio.md) | TBD |
| [IOCTL_CDROM_GET_DRIVE_GEOMETRY IOCTL](ni-ntddcdrm-ioctl-cdrom-get-drive-geometry.md) | TBD |
| [IOCTL_CDROM_SET_VOLUME IOCTL](ni-ntddcdrm-ioctl-cdrom-set-volume.md) | TBD |
| [IOCTL_CDROM_GET_CONFIGURATION IOCTL](ni-ntddcdrm-ioctl-cdrom-get-configuration.md) | TBD |
| [IOCTL_CDROM_RAW_READ IOCTL](ni-ntddcdrm-ioctl-cdrom-raw-read.md) | TBD |
| [IOCTL_CDROM_READ_TOC IOCTL](ni-ntddcdrm-ioctl-cdrom-read-toc.md) | TBD |
| [IOCTL_CDROM_CHECK_VERIFY IOCTL](ni-ntddcdrm-ioctl-cdrom-check-verify.md) | TBD |
| [IOCTL_CDROM_STOP_AUDIO IOCTL](ni-ntddcdrm-ioctl-cdrom-stop-audio.md) | TBD |

This header is used in these topics:

- [Storage](..content/_Storage)
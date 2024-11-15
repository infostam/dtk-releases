# diagport toolkit (dtk)

The **diagport toolkit** (dtk) Windows application is a tool communicating with Qualcomm-based smartphones and CPE modems, allowing to capture raw 2G/3G/4G/5G radio frames. The tool uses the Qualcomm diagnostic protocol, also called QCDM (Qualcomm Diagnostic Monitor) to communicate with the device. It allows us to generate packets captures in PCAP file format using either an Android smartphone or a modem.

Additionally, it is capable of decoding 5G frames and create decoded PCAPNG files can be used and interpreted by any network protocol analyzer application which handles this type of file format.

### Prerequisites

Generally, there are certain prerequisites which are required before the **diagport toolkit** can be used:

- It is only compatible with devices which has Qualcomm chipset.
- The Diag Port of the device must be enabled for capturing to expose it over USB.
- Windows drivers of the device required to be able to recognize and use the opened Diag Port for tracing.
- It runs on Windows OS only.
- Wireshark with Npcap is required.
- It requires a license.

Fulfilling these requirements is the responsibility of the end user.

## File Converter

In order to use the **File Converter** tool, click on the `Open` button, select a PCAP file with proprietary 5G frames to convert, and click on the `Convert` button.

Once the conversion completed, a new PCAPNG file is generated with the same name as the source file with an additional *_decoded* string, stored in the same folder as the source file, contains the decoded 5G frames along with all the other packets, and a popup message is shown. The number of successfully decoded packets is also mentioned.

In case the source file has the 5G frames on a different UDP port (not the default 49999 used by the application), add that port to the input field before conversion to identify the proprietary packets.

**Note**, only one application can communicate with the device’s Diag port at the same time.

## UE Capture

In order to use the **UE Capture** tool, select a device and a module from the drop-down lists, 
add an output capture filename if `pcap` module was selected and include IP traffic if required.

**Note**, the filename should include file extension too such as `output.pcap`.

The device dropdown list contains all the COM ports related to the device which are also visible in `Device Manager`. This list has all the name of the pseudo-serial device as the COM port on Windows (such as COM2, COM3), allows the tool to connect to the Qualcomm diagnostics port over a pseudo-serial port over USB, independently from ADB, which is the most common way to connect to the Qualcomm Diag protocol of an Android-based phone using an external device. The Qualcomm diagnostic port must be enabled on the device.

The module dropdown list contains 3 options:
- `pcap` is for writing packets to a PCAP file automatically.
- `wireshark-live` is for opening Wireshark and see frames in real-time.
- `info` is for generic information about the device which is printed under Execution Output.

By default, the IP traffic sent by the device is not included, only the signaling frames captured. The IP traffic generated by the device can be captured with selecting IP traffic included from the drop-down list. Note, IP being barely the layer 3 for the data traffic in 2G/3G/4G/5G, at the detail that its headers may be compressed (ROHC) and a tiny PPP header may be included.

The data traffic the device sends uses a channel different from the signaling traffic, this channel is setup through the signaling traffic; the tool should thus show all details relevant to how this channel is initiated.

The *Save Output* button saves the Execution Output content into a text file under the `logs` folder.

The *Copy Output* button copies the Execution Output content to the clipboard.

The *Clear Output* button clears and resets the Execution Output after a confirmation warning.

## Licensing and Upgrade

### Fundamentals

The **diagport toolkit** is a commercialized application for telecom specific troubleshooting and engineering purpose. Only paid versions are available which require a time-based license subscription (e.g. annual subscription). As long as the subscription is active the application support and upgrade are automatically included.

### License

The end user subscription is controlled via a license (Serial Key) which is generated with a code related to the computer hardware and therefore, the license is not transferrable automatically. In case of license transfer is required (e.g. the computer is replaced), the license must be regenerated.

The License frame shows the
- Unique Service ID.
- The remaining days of the current license.
- The Serial Key via the placeholder text of an entry field.

The *Copy Service ID* button copies the service ID to the clipboard.

The *Set License* button stores a license provided in the entry field.

The *Remove License* button deletes the earlier stored license.

Additionally, the *Collect Logs* button is used for collecting history logs of the application executions.

## License
[infostam Pte. Ltd.](https://www.infostam.com)
All rights reserved.
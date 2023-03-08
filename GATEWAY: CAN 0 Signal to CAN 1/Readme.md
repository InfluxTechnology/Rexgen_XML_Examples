# XML Example:GATEWAY:CAN 0 Signal to CAN 1.

In this example, we will see how we can configure a ReXgen data logger to transfer CAN Signal from CAN 0 Bus to CAN 1 Bus

## Documentation

Below image shows how each element are linked in the XML file.

[XML\_Link]https://itltdgithub.s3.ap-south-1.amazonaws.com/gatewaycan0can1.png

They are connected using Unique IDs (UID).
	
### Default Settings

* CAN Baud Rate: 500 Kbps
* CAN Signals Routed from CAN ID 0x420 and 0x600 to 0x7B

#### Following parameters can be modified by editing the XML as required.

**Modifying CAN Bus Channel:**

Edit the value of the PhysicalNumber element in the XML file under the CAN interface block.
0 for CAN 0, 1 for CAN 1, 2 for CAN 2 and 3 for CAN 3

```xml
<CANINTERFACE UID="2">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```
** Modifying CAN Baud Rate:**

Edit the value of the CANBusSpeed element in the XML file under the CAN interface block.
Value has to be specified in bps

```xml
<CANINTERFACE UID="4">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```
**Modifying the CAN Identifier for the messages:**
Edit the values of MessageIdentStart and MessageIdentEnd Elements under the CANMESSAGE block for the message you wish to edit. Please note that the example DBC will be invalid after this change.

Value has to be entered in Decimal

```xml
<CANMESSAGE_LIST>
      <CANMESSAGE UID="4">
        <MessageIdentStart>299</MessageIdentStart>
        <MessageIdentEnd>299</MessageIdentEnd>
        <Direction>OutputPeriodic</Direction>
        <DLC>8</DLC>
        <IsExtended>false</IsExtended>
```
**Modifying the CAN Message transmission period:**

Edit the values of Period Elements under the CANMESSAGE block for the message you wish to edit.

Value has to be entered in milliseconds

```xml
<CANMESSAGE_LIST>
      <CANMESSAGE UID="4">
        <MessageIdentStart>299</MessageIdentStart>
        <MessageIdentEnd>299</MessageIdentEnd>
        <Direction>OutputPeriodic</Direction>
        <DLC>8</DLC>
        <IsExtended>false</IsExtended>
        <InterfaceUID>4</InterfaceUID>
        <Period>100</Period>
```

**Modifying the CAN Signal Properties:**
The following properties can be modified:

•	StartBit
•	Bit Count
•	Endian
•	Default Value
•	Par A (Scaling)
•	Par B (Offset)
•	Signal Type
•	Signal Name

```xml
<CANSIGNAL UID="6">
        <InputType>MESSAGE</InputType>
        <InputUID>4</InputUID>
        <MessageUID>4</MessageUID>
        <StartBit>0</StartBit>
        <BitCount>16</BitCount>
        <Endian>INTEL</Endian>
        <DefaultValue>0</DefaultValue>
        <ParA>1</ParA>
        <ParB>0</ParB>
        <SignalType>UNSIGNED</SignalType>
        <Name>Signal1</Name>
      </CANSIGNAL>
```

#### User can load the XML file into the ReXgen logger using ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL

Process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open

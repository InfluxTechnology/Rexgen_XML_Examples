# XML Example:Transmitting GNSS Data Over CAN Bus and recording in eMMC.

IIn this example we will see how we can configure a ReXgen data logger to transmit the GNSS positioning data over the CAN Bus and record the GNSS data in the internal storage.

## Following GNSS Data will be transmitted via CAN 0 Bus and recorded in internal memory:

Latitude
Longitude
Altitude
Speed Over Ground
Ground Distance
Course Over Ground
Number Of Satellites
Quality

## Documentation

the below image shows how each element are linked in the XML file.

![image](https://user-images.githubusercontent.com/122855530/223619823-cb30d70c-d55d-4b10-b658-5a250530ab94.png)

They are connected using Unique IDs (UID).
	
### Default Settings

* CAN Baud Rate: 500 Kbps
* GNSS Sampling Rate: 100ms
* CAN ID For various signals:
* 0x12B – Altitude, GPS Speed
* 0x12C – Longitude, Latitude
* 0x12D – Ground Distance
* 0x12E – Number Of Satellites, Course
* 0x12F - Quality

Example DBC provided with XML.


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
**Modifying CAN Baud Rate:**

Edit the value of the CANBusSpeed element in the XML file under the CAN interface block.
Value has to be specified in bps

```xml
<CANINTERFACE UID="2">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```
**Modifying GNSS Sampling Rate:**

Edit the value of the SamplingRate element under the GNSSINTERFACE Block

Value has to be specified in milliseconds

```xml
<GNSSINTERFACE UID="3">
        <PhysicalNumber>0</PhysicalNumber>
        <SamplingRate>100</SamplingRate>
 </GNSSINTERFACE>
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

#### User can load the XML file into the ReXgen logger using ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL

Process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open

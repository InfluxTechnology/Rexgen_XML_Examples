# GNSS Data Transmission Over CAN Bus.

This example shows how we can configure a ReXgen data logger to transmit the GNSS positioning data over the CAN Bus.

### Use Cases

* Easily inject real-time location information into your CAN Bus.
* Feed real-time location information to your CAN Dashboard or Instrument Cluster.
* Use ReXgen as a GNSS module for your existing CAN data logger.

### Following GNSS Data will be transmitted via CAN 0 Bus:

* Latitude
* Longitude
* Altitude
* Speed Over Ground
* Ground Distance
* Course Over Ground
* Number Of Satellites
* Quality

## Documentation

The below image shows how each element is linked in the XML file.

![XML\_Link](https://itltdgithub.s3.ap-south-1.amazonaws.com/gnss2canonly.png)

They are connected using Unique IDs (UIDs).

### Default Settings

* CAN Baud Rate: 500 Kbps
* GNSS Sampling Rate: 100ms
* CAN ID For various signals:
* 0x12B – Altitude, GPS Speed
* 0x12C – Longitude, Latitude
* 0x12D – Ground Distance
* 0x12E – Number Of Satellites, Course
* 0x12F - Quality Example DBC provided with XML.

#### These parameters can be modified by editing the XML as required.

**Modifying CAN Bus Channel:**

Edit the value of the PhysicalNumber element in the XML file under the CAN interface block. 0 for CAN 0, 1 for CAN 1, 2 for CAN 2 and 3 for CAN 3

```xml
<CANINTERFACE UID="1">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```

**Modifying CAN Baud Rate:**

Edit the value of the CANBusSpeed element in the XML file under the CAN interface block. Value has to be specified in bps

```xml
<CANINTERFACE UID="1">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```

**Modifying GNSS Sampling Rate:**

Edit the value of the SamplingRate element under the GNSSINTERFACE Block Value has to be specified in milliseconds

```xml
<GNSSINTERFACE UID="2">
        <PhysicalNumber>0</PhysicalNumber>
        <SamplingRate>100</SamplingRate>
 </GNSSINTERFACE>

```

**Modifying the CAN Identifier for the messages:**

noteEdit the values of MessageIdentStart and MessageIdentEnd Elements under the CANMESSAGE block for the message you wish to edit. Please not that the example DBC will be invalid after this change.

Value has to be entered in Decimal

```xml
<CANMESSAGE_LIST>
      <CANMESSAGE UID="3">
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
      <CANMESSAGE UID="3">
        <MessageIdentStart>299</MessageIdentStart>
        <MessageIdentEnd>299</MessageIdentEnd>
        <Direction>OutputPeriodic</Direction>
        <DLC>8</DLC>
        <IsExtended>false</IsExtended>
        <InterfaceUID>4</InterfaceUID>
        <Period>100</Period>
```

#### Users can load the XML file into the ReXgen logger using the ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL.

The process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><mark style="color:blue;">GitHub Link</mark></td><td><a href="https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/GNSS_to_CAN">https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/GNSS_to_CAN</a></td></tr><tr><td><mark style="color:blue;">XML file</mark></td><td><a href="GNSS2CAN_Only.xml">GNSS2CAN_Only.xml</a></td></tr><tr><td><mark style="color:blue;">DBC file</mark></td><td><a href="ReXgen_IMU_Out_V3.dbc">ReXgen_IMU_Out_V3.dbc</a></td></tr></tbody></table>

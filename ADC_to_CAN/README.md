# ADC Data Transmission Over CAN Bus.

This example explains configuring a ReXgen data logger to transmit the ADC data over the CAN Bus.

### Following ADC Data will be transmitted via CAN 0 Bus:

ADC 0 ADC 1

## Documentation

The below image shows how each element are linked in the XML file.

![](https://itltdgithub.s3.ap-south-1.amazonaws.com/adc2canonly.png)

They are connected using Unique IDs (UID).

### Default Settings

* CAN Baud Rate: 500 Kbps
* ADC Sampling Rate: 100ms
* CAN ID For various signals:
* 0x12A – ADC 0 & ADC 1
* Example DBC provided with XML.

#### Following parameters can be modified by editing the XML as required.

**Modifying CAN Bus Channel:**

Edit the value of the PhysicalNumber element in the XML file under the CAN interface block. 0 for CAN 0, 1 for CAN 1, 2 for CAN 2 and 3 for CAN 3

```xml
<CANINTERFACE UID="4">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```

**Modifying CAN Baud Rate:**

Edit the value of CANBusSpeed element in the XML file under the CAN interface block. Value has to be specified in bps

```xml
<CANINTERFACE UID="4">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```

**Modifying ADC Sampling Rate:**

Edit the value of SamplingRate element under the ADC list Block Value has to be specified in milliseconds

```xml
<ADC UID="2">
        <PhysicalNumber>0</PhysicalNumber>
        <Rate>100</Rate>
		<ParA>1<ParA>
		<ParB>0<ParB>
 </ADC>

```

**Specifying the ADC Factor and Offset:**

Par A specifies the Factor, and Par B specifies the Offset.

```xml
<ADC UID="6">
       <PhysicalNumber>0</PhysicalNumber>
        <Rate>100</Rate>
		<ParA>1<ParA>
		<ParB>0<ParB>
 </ADC>
```

**Modifying the CAN Message transmission period:**

Edit the values of MessageIdentStart and MessageIdentEnd Elements under the CANMESSAGE block for the message you wish to edit. Please note that the example DBC will be invalid after this change.

Value has to be entered in Decimal

```xml
<CANMESSAGE_LIST>
      <CANMESSAGE UID="36">
        <MessageIdentStart>299</MessageIdentStart>
        <MessageIdentEnd>299</MessageIdentEnd>
        <Direction>OutputPeriodic</Direction>
        <DLC>8</DLC>
        <IsExtended>false</IsExtended>
       
```

**Modifying the CAN Message transmission period:**

Edit the values of Period Elements under the CANMESSAGE block for the message you wish to edit. Value has to be entered in milliseconds

```xml
<CANMESSAGE_LIST>
      <CANMESSAGE UID="36">
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

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><mark style="color:blue;">GitHub Link</mark></td><td><a href="https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/ADC_to_CAN">https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/ADC_to_CAN</a></td></tr><tr><td><mark style="color:blue;">XML</mark></td><td><a href="ADC2CAN_Only.xml">ADC2CAN_Only.xml</a></td></tr><tr><td><mark style="color:blue;">Dbc file</mark></td><td><a href="ReXgen_IMU_Out_V3.dbc">ReXgen_IMU_Out_V3.dbc</a></td></tr></tbody></table>

# RTC Data To CAN Bus

### This example explains configuring a ReXgen data logger to transmit the RTC data over the CAN Bus.

### Documentation

The below image shows how each element is linked in the XML file.

<div align="left">

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="226"><figcaption></figcaption></figure>

</div>

They are connected using Unique IDs (UID).

### Default Settings:

CAN Baud Rate: 500 Kbps

Example DBC provided with XML.

### The following parameters can be modified by editing the XML as required.

**Modifying MaxlogSize and MaxLogTime:**

Edit the values of MaxLogSize and MaxLogTime (in seconds) Elements under the SDINTERFACE block for the message you wish to edit.

```xml
<SDINTERFACE_LIST>
      <SDINTERFACE UID="2">
        <MaxLogSize>104857600</MaxLogSize>
        <MaxLogTime>3600</MaxLogTime>
```

**Modifying CAN Bus Channel:**

Edit the value of the PhysicalNumber to change the channel number to 0, 1, 2 or 3

Modify the CANBusSpeed element in the XML file under the CAN interface block to modify the CAN bus baud rate.

Value has to be specified in bps

```xml
<CANINTERFACE UID="4">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>    
```

**Modifying the CAN Message and Transmission period:**

Edit the MessageIdentStart and MessageIdentEnd Elements values under the CANMESSAGE block for the message ID you wish to transmit to the RTC.

Modify the Transmission period by editing the value of the Period in the XML.

Please note that the example DBC will be invalid after this change.

```xml
<CANMESSAGE UID="42">
        <MessageIdentStart>516</MessageIdentStart>
        <MessageIdentEnd>516</MessageIdentEnd>
        <Direction>OutputPeriodic</Direction>
        <DLC>8</DLC>
        <IsExtended>false</IsExtended>
        <InterfaceUID>4</InterfaceUID>
        <Period>1000</Period>
```

**Modifying the Sampling Rate:**

Edit the values of the Sampling Rate under the INTERNAL\_PARAMETER block for the message you wish to edit. Please note that the example DBC will be invalid after this change.

```xml
<INTERNAL_PARAMETER UID="1200">
                              <InputUID>0</InputUID>
                   <Parameter_Type>RTC</Parameter_Type>
        <Value_Type>ULONG</Value_Type>
        <SamplingRate>1000</SamplingRate
```

**Modifying the CAN Signal:**

Edit the StartBit and Bit Count Elements values under the CANSIGNAL block for the message you wish to edit. Please note that the example DBC will be invalid after this change.

```xml
<CANSIGNAL UID="44">
        <InputType>COMMON</InputType>
        <InputUID>1200</InputUID>
        <MessageUID>42</MessageUID>
        <StartBit>7</StartBit>
        <BitCount>32</BitCount>  
```

#### Users can load the XML file into the ReXgen logger using the ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL.

The process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><mark style="color:blue;">GitHub Link</mark></td><td><a href="https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/RTC_DATA_TO_CAN_BUS">https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/RTC_DATA_TO_CAN_BUS</a></td></tr><tr><td><mark style="color:blue;">XML file</mark></td><td><a href="RTC2CAN.xml">RTC2CAN.xml</a></td></tr><tr><td><mark style="color:blue;">DBC file</mark></td><td><a href="RTC2CAN.dbc">RTC2CAN.dbc</a></td></tr></tbody></table>

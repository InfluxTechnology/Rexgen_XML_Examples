# IMU Data Transmission Over CAN Bus.

This example shows how we can configure a ReXgen data logger to transmit IMU data over the CAN Bus.

### Following IMU Data will be transmitted via CAN 0 Bus:

Accelerometer X Accelerometer Y Accelerometer Z

Gyroscope X Gyroscope Y Gyroscope Z

## Documentation

The below image shows how each element are linked in the XML file.

![](<../.gitbook/assets/image (2).png>)

They are connected using Unique IDs (UID).

### Default Settings

* CAN Baud Rate: 500 Kbps
* ADC Sampling Rate: 100ms
* CAN ID For various signals:
* 0x128 – Accelerometer
* 0x129 – Gyroscope
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

Edit the value of CANBusSpeed element in the XML file under the CAN interface block.

Value has to be specified in bps

```xml
<CANINTERFACE UID="4">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```

**Modifying Accelerometer Sampling Rate:**

Edit the value of SamplingRate element under the ACCELEROMETER list Block.

Value has to be specified in milliseconds

```xml
<ACCELEROMETER UID="4">
        <PhysicalNumber>0</PhysicalNumber>
        <Axis>X</Axis>
        <SamplingRate>10</SamplingRate>
```

**Modifying Gyroscope Sampling Rate:**

Edit the value of the SamplingRate element under the GYRO LIST Block

Value has to be specified in milliseconds

```xml
<GYRO UID="7">
        <PhysicalNumber>0</PhysicalNumber>
        <Axis>X</Axis>
        <SamplingRate>10</SamplingRate>
```

**Modifying Accelerometer High Low Range:**

Edit the value of the SamplingRate element under the ACCELEROMETER LIST Block

Value has to be specified in milliseconds

```xml
<ACCELEROMETER UID="6">
        <PhysicalNumber>0</PhysicalNumber>
        <Axis>Z</Axis>
        <SamplingRate>10</SamplingRate>
        <RangeHi>16</RangeHi>
        <RangeLow>-16</RangeLow>
      </ACCELEROMETER>
```

**Modifying Gyroscope Sampling Rate:**

Edit the value of the SamplingRate element under the GYRO LIST Block

Value has to be specified in milliseconds

```xml
<GYRO UID="7">
        <PhysicalNumber>0</PhysicalNumber>
        <Axis>X</Axis>
        <SamplingRate>10</SamplingRate>
        <RangeHi>500</RangeHi>
        <RangeLow>-500</RangeLow>
      </GYRO>
```

**Modifying the CAN Identifier for the messages:**

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

Edit the values of Period Elements under the CANMESSAGE block for the message you wish to edit.

Value has to be entered in milliseconds

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

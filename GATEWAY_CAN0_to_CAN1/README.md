# Gateway Routing CAN0 to CAN1.

In this example, we will see how we can configure a ReXgen data logger to route all the CAN traffic from CAN 0 Bus to CAN 1 Bus

## Documentation

Below image shows how each element are linked in the XML file.

<div align="left">

<img src="https://user-images.githubusercontent.com/122855530/223421344-baee66c2-ccb6-42d7-8fc0-94dd25ded313.png" alt="image" width="188">

</div>

They are connected using Unique IDs (UID).

### Default Settings

* CAN Baud Rate: 500 Kbps
* All CAN IDs are Routed

#### The following parameters can be modified by editing the XML as required.

**Modifying CAN Baud Rate:**

Edit the value of the CANBusSpeed element in the XML file under the CAN interface block. Value has to be specified in bps

```xml
<CANINTERFACE UID="4">
        <Type>CAN</Type>
        <PhysicalNumber>0</PhysicalNumber>
        <CANBusSpeed>500000</CANBusSpeed>
        <CANFDBusSpeed>8000000</CANFDBusSpeed>
        <CANFDNonISO>false</CANFDNonISO>
```

#### Users can load the XML file into the ReXgen logger using the ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL.

The process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><mark style="color:blue;">GitHub link</mark></td><td><a href="https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/GATEWAY_CAN0_to_CAN1">https://github.com/InfluxTechnology/Rexgen_XML_Examples/tree/main/GATEWAY_CAN0_to_CAN1</a></td></tr><tr><td><mark style="color:blue;">XML file</mark></td><td><a href="Gateway_CAN0_to_CAN1.xml">Gateway_CAN0_to_CAN1.xml</a></td></tr><tr><td><mark style="color:blue;">DBC file</mark></td><td><a href="ReXgen_IMU_Out_V3.dbc">ReXgen_IMU_Out_V3.dbc</a></td></tr></tbody></table>

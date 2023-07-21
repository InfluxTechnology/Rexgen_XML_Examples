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
* All Can ids are Routed

#### Following parameters can be modified by editing the XML as required.

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

#### User can load the XML file into the ReXgen logger using ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL

Process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open

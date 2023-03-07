# XML Example:GATEWAY: CAN 0 to CAN 1.

In this example, we will see how we can configure a ReXgen data logger to route all the CAN traffic from CAN 0 Bus to CAN 1 Bus

## Documentation

Below image shows how each element are linked in the XML file.

[XML\_Link]https://itltdgithub.s3.ap-south-1.amazonaws.com/gatewaycan0can1.png

They are connected using Unique IDs (UID).

### Default Settings

* CAN Baud Rate: 500 Kbps
* All Can ids are Routed

#### Following parameters can be modified by editing the XML as required.

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

#### User can load the XML file into the ReXgen logger using ReXdesk application/ReXdesk Convert application or the Rxlibrary DLL

Process to send XML to logger using ReXdesk. Click on Config Menu > Run > Run Config Using External File > Browse the XML file and click Open

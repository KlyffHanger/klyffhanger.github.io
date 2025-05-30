
{% assign deviceName = page.title | remove: "How to connect " | remove: "to Klyff?" %}
{% assign deviceVendorLink = "https://www.milesight-iot.com/lorawan/gateway/ug56/" %}
{% assign thingsboardHost = "https://" | append: hostName %}
{% assign prerequisites = '
- <a href="' | append: deviceVendorLink | append: '" target="_blank">' | append: deviceName | append: '</a>
- [UG56 gateway user manual](https://resource.milesight.com/milesight/iot/document/ug56-user-guide-en.pdf){: target="_blank"}
- [Network Server account](#configuration)
'
 %}

## Introduction

![{{deviceName}}](/images/devices-library/{{page.deviceImageFileName}}){: style="float: left; max-width: 200px; max-height: 200px; margin: 0px 10px 0px 0px"}
[UG56 LoRaWAN® Gateway]({{deviceVendorLink}}){: target="_blank"} is a high-performance 8-channel LoRaWAN® gateway that offers reliable connectivity for industrial applications.

Industrial-Grade Design
Listen Before Talk
Gateway Fleet

Free Embedded Network Server
Multiple Backhaul Connectivities
Global LoRaWAN® Frequency Plans:
RU864/IN865/EU868/AU915/US915/KR920/AS923

{% assign feature = "Platform Integrations" %}{% include templates/pe-feature-banner.md %}

After doing steps described in this guide you will have a connected and configured gateway on a network server and integration on Klyff, it will allow you to add devices, receive data from them and process a data.

## Prerequisites

To continue with this guide we will need the following:
{{ prerequisites }}
- [Klyff account]({{ thingsboardHost }}){: target="_blank"}

## Gateway connection

According to the [official user manual](https://resource.milesight.com/milesight/iot/document/ug56-user-guide-en.pdf){: target="_blank"} and [this guide](https://support.milesight-iot.com/support/solutions/articles/73000514278-how-to-connect-milesight-gateway-to-the-internet){: target="_blank"} you can connect the gateway to the network and get access to the WebUI in two ways:

- Wireless connection:
  1. Enable Wireless Network Connection on your computer and search for access point "Gateway_******" to connect it.
  2. Open a Web browser on your PC and type in the IP address **192.168.1.1** to access the web GUI.
  3. Enter the username(Default: **admin**) and password(Default: **password**), click "**Login**".

- Wired connection:
  Connect PC to UG56 Ethernet port directly or through PoE injector to access the web GUI of gateway. The following steps are based on Windows 10 system for your reference.

  1. Go to the "Control Panel" → "Network and Internet" → "Network and Sharing Center", then click "Ethernet" (May have different names).
  2. Go to the "Properties" → "Internet Protocol Version 4(TCP/IPv4)" and select "Use the following IP address", then assign a static IP manually within the same subnet of the gateway.
  3. Open a Web browser on your PC and type in the IP address **192.168.23.150** to access the web GUI.
  4. Enter the username and password, click **"Login"**.

{% assign gatewayGeneralSettings = '
    ===
        image: /images/devices-library/ready-to-go-devices/milesight-lorawan-gateway/general-settings-view.png,
        title: Now you have ability to configure the gateway.
'%}

Now you have ability to configure the gateway.

{% include images-gallery.liquid imageCollection=gatewayGeneralSettings %}

Go to the "**Packet Forwarder**" page in the left menu and save '**Gateway EUI**' and '**Gateway ID**' values. By default, Gateway EUI and Gateway ID are the same. We will need them to create a gateway on network server.

{% assign gatewayPacketForwarderTab = '
    ===
        image: /images/devices-library/ready-to-go-devices/milesight-lorawan-gateway/ns-configuration-before.png,
        title: Open "**Packet Forwarder**" in the left menu and save '**Gateway EUI**' and '**Gateway ID**', we will need them to create a gateway on network server.
'%}

{% include images-gallery.liquid imageCollection=gatewayPacketForwarderTab %}

Next steps will describe how to connect the gateway to network server.

## Configuration

To create an integration with a network server please choose first one of the supported network servers:

{% assign targetIntegrationTypes = '
ChirpStack,
TheThingsStack,
TheThingsIndustries,
Loriot
'%}

{% include /docs/devices-library/blocks/basic/thingsboard-create-integration-block.liquid target-integration-types=targetIntegrationTypes %}

## Conclusion

{% include /docs/devices-library/blocks/basic/lora-gateway-conclusion-block.md %}
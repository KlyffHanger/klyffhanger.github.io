{% assign deviceName = page.title | remove: "How to connect " | remove: "to Klyff?" %}
{% assign prerequisites = "
- " | append: deviceName | append: "
- [tb-mqtt-client library](https://pypi.org/project/tb-mqtt-client/)
- [python ≥ 3.7](https://www.python.org/)
- [Adafruit-Blinka](https://pypi.org/project/Adafruit-Blinka/) "
 %}

## Introduction
![{{deviceName}}](/images/devices-library/{{page.deviceImageFileName}}){: style="float: left; max-width: 200px; max-height: 200px; margin: 0px 10px 0px 0px"}
BeagleBone Black is a low-cost, community-supported development platform suitable for both professionals and hobbyists. 
Boot into Linux in less than 10 seconds and start developing your projects with just one USB cable.
The BeagleBone Black is the latest addition to the BeagleBoard.org family and, like its predecessors, is aimed at the 
open-source development community, early adopters, and anyone interested in a low-cost ARM Cortex-A8-based processor. 
It was equipped with a minimal set of features to allow the user to experience the power of the processor, and is not 
intended as a full-fledged development platform, as many functions and interfaces provided by the processor are not 
available with the BeagleBone Black through the embedded system. It is not a complete product designed to perform any 
specific function. This is the basis for experiments and learning to program the processor and access peripheral devices 
by creating your own software and hardware. It also offers access to many interfaces and allows the use of additional 
expansion boards to add many different combinations of functions. The user can also design his own board or add his own 
circuits.

{% include /docs/devices-library/blocks/basic/introduction-block.md %}

## Create device on Klyff

{% include /docs/devices-library/blocks/basic/thingsboard-create-device-block.md %}

## Install required libraries and tools

{% include /docs/devices-library/blocks/single-board-computers/install-required-libraries-and-tools-block.md %}

## Connect device to Klyff

{% include /docs/devices-library/blocks/basic/thingsboard-provide-device-access-token-block.md %}

{% include /docs/devices-library/blocks/single-board-computers/general-code-to-program-block.md %}

## Synchronize device state using client and shared attribute requests

{% include /docs/devices-library/blocks/single-board-computers/thingsboard-synchronize-device-state-using-attribute-requests-block.md %}

## Check data on Klyff

{% include /docs/devices-library/blocks/single-board-computers/check-data-on-thingsboard-block.md %}

## Control device using shared attributes

{% include /docs/devices-library/blocks/single-board-computers/update-shared-attributes-block.md %}

## Control device using RPC

{% include /docs/devices-library/blocks/single-board-computers/using-rpc-block.md %}

## Conclusion

{% include /docs/devices-library/blocks/basic/conclusion-block.md %}
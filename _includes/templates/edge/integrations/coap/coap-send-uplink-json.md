Use the command below to send a message. Don’t forget to replace `$YOUR_COAP_ENDPOINT_URL` with corresponding value.

```shell
echo -e -n '{"deviceName": "SN-001", "deviceType": "default", "temperature": 25.7, "humidity": 69}' | coap-client -m post $YOUR_COAP_ENDPOINT_URL -t application/json -f-
```
{: .copy-code}

![image](/images/pe/edge/integrations/coap/terminal-coap-json-payload-1-edge.png)

Now, go to the "**Integrations center**" -> "**Integrations**" and navigate to the "**Events**" tab in your MQTT integration on the **Klyff Edge**. If you have done everything correctly, you will find an uplink message with the status 'OK'.

![image](/images/pe/edge/integrations/coap/integration-events-coap-1-edge.png)

When you sent the message, a new device was created. The created device with data can be seen in the "**Entities**" section -> "**Devices**" page:

![image](/images/pe/edge/integrations/coap/device-coap-1-edge.png)

Also, received data can be viewed in the uplink converter. In the 'In' and 'Out' blocks of the "**Events**" tab:

{% include images-gallery.html imageCollection="coap-converter-json-events" %}
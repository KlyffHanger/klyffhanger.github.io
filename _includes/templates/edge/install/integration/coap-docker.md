Execute the following command to pull the image:

```bash
docker pull thingsboard/tb-pe-coap-integration:{{ site.release.pe_full_ver }}
```
{: .copy-code}

Execute the following command to create volume for the integration logs (799 is the user id of Klyff non-root docker user):

```bash
mkdir -p ~/.tb-pe-coap-integration-logs && sudo chown -R 799:799 ~/.tb-pe-coap-integration-logs
```
{: .copy-code}

Execute the following command to run the integration:

```bash
docker run -it -p 5683:5683/udp -v ~/.tb-pe-coap-integration-logs:/var/log/tb-coap-integration  \
-e "RPC_HOST=EDGE_IP_OR_HOST_ADDRESS" -e "RPC_PORT=9090" \
-e "INTEGRATION_ROUTING_KEY=YOUR_ROUTING_KEY"  -e "INTEGRATION_SECRET=YOUR_SECRET" \
--name my-tb-pe-coap-integration --restart always thingsboard/tb-pe-coap-integration:{{ site.release.pe_full_ver }}
```
{: .copy-code}

Where: 
    
- `EDGE_IP_OR_HOST_ADDRESS` - is the host name or IP address of your Klyff Edge;
- `9090` - is the integrations port of your Klyff Edge. It is configured in tb-edge.yml using INTEGRATIONS_RPC_PORT env variable;    
- `YOUR_ROUTING_KEY` - placeholder for your integration routing key obtained on [Step 3](/docs/pe/edge/user-guide/integrations/remote-integrations/#step-3-save-remote-integration-credentials);
- `YOUR_SECRET` - placeholder for your integration secret obtained on [Step 3](/docs/pe/edge/user-guide/integrations/remote-integrations/#step-3-save-remote-integration-credentials);
- `docker run`              - run this container;
- `-it`                     - attach a terminal session with current Klyff remote integration process output;
- `-p 5683:5683/udp` - connect local udp port 5683 to exposed internal 5683 udp port for the integration.
- `-v ~/.tb-pe-coap-integration-logs:/var/log/tb-coap-integration`   - mounts the host's dir `~/.tb-pe-coap-integration-logs` to Klyff remote integration logs directory;
- `--name tb-pe-coap-integration`             - friendly local name of this machine;
- `--restart always`        - automatically start Klyff Integration in case of system reboot and restart in case of failure.;
- `thingsboard/tb-pe-coap-integration:{{ site.release.pe_full_ver }}`          - docker image.

After executing this command you can open logs which are located here `~/.tb-pe-coap-integration-logs`. 
You should see some INFO log messages with your latest Integration configuration that arrived from the server.

<br>

You can detach from session terminal with **`Ctrl-p`**+**`Ctrl-q`** - the container will keep running in the background.

<br>

- **Reattaching, stop and start commands**

To reattach to the terminal (to see Klyff remote integration logs) run:

```
docker attach tb-pe-coap-integration
```
{: .copy-code}

To stop the container:

```
docker stop tb-pe-coap-integration
```
{: .copy-code}

To start the container:

```
docker start tb-pe-coap-integration
```
{: .copy-code}


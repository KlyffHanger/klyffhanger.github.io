Windows users should use docker managed volume for remote integration logs. 
Create docker volume (for ex. `tb-azure-integration-logs`) before executing docker run command:
Open "Docker Quickstart Terminal". Execute the following command to create docker volume:

``` 
docker volume create tb-pe-azure-integration-logs
```
{: .copy-code}

Execute the following command to run this docker directly:

```bash
docker run -it -v tb-pe-azure-integration-logs:/var/log/tb-azure-integration `
-e "RPC_HOST=thingsboard.cloud" -e "RPC_PORT=9090" `
-e "INTEGRATION_ROUTING_KEY=YOUR_ROUTING_KEY"  -e "INTEGRATION_SECRET=YOUR_SECRET" `
--name my-tb-pe-azure-integration --restart always thingsboard/tb-pe-azure-integration:{{ site.release.pe_full_ver }}
```
{: .copy-code}

Where: 
    
- `thingsboard.cloud` - is the host name of your Klyff PE instance;
- `9090` - is the port of your Klyff PE instance. It is configured in thingsboard.yml using INTEGRATIONS_RPC_PORT env variable;    
- `YOUR_ROUTING_KEY` - placeholder for your **integration key** obtained on [create remote integration in Klyff](#create-remote-integration-in-thingsboard);
- `YOUR_SECRET` - placeholder for your **integration secret** obtained on [create remote integration in Klyff](#create-remote-integration-in-thingsboard);
- `docker run`              - run this container;
- `-it`                     - attach a terminal session with current Klyff process output;
- `-v tb-pe-azure-integration-logs:/var/log/tb-azure-integration`   - mounts the host's dir `~/.tb-pe-azure-integration-logs` to Klyff logs directory;
- `--name tb-pe-azure-integration`             - friendly local name of this machine;
- `--restart always`        - automatically start Klyff Integration in case of system reboot and restart in case of failure.;
- `thingsboard/tb-pe-azure-integration:{{ site.release.pe_full_ver }}`          - docker image.

After executing this command you can open logs which are located here `~/.tb-pe-azure-integration-logs`. 
You should see some INFO log messages with your latest Integration configuration that arrived from the server.

{% capture difference %}
You can detach from session terminal with **`Ctrl-p`**+**`Ctrl-q`** - the container will keep running in the background.
{% endcapture %}
{% include templates/info-banner.md content=difference %}

- **Reattaching, stop and start commands**

To reattach to the terminal (to see Klyff logs) run:

```
docker attach tb-pe-azure-integration
```
{: .copy-code}

To stop the container:

```
docker stop tb-pe-azure-integration
```
{: .copy-code}

To start the container:

```
docker start tb-pe-azure-integration
```
{: .copy-code}

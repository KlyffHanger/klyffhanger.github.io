Download installation package:

```bash
wget https://dist.thingsboard.io/tb-opc-ua-integration-{{ site.release.pe_ver }}.deb
```
{: .copy-code}

Install integration as a service:

```bash
sudo dpkg -i tb-opc-ua-integration-{{ site.release.pe_ver }}.deb
```
{: .copy-code}

Open the file for editing using the following command:

```bash 
sudo nano /etc/tb-opc-ua-integration/conf/tb-opc-ua-integration.conf
``` 
{: .copy-code}

Locate the following configuration block:

```bash
# UNCOMMENT NEXT LINES AND PUT YOUR CONNECTION PARAMETERS:
# export RPC_HOST=thingsboard.cloud
# export RPC_PORT=9090
# export INTEGRATION_ROUTING_KEY=YOUR_INTEGRATION_KEY
# export INTEGRATION_SECRET=YOUR_INTEGRATION_SECRET
```

and put your configuration parameters. Please don't forget to uncomment the export statement. See example below:

```bash
# UNCOMMENT NEXT LINES AND PUT YOUR CONNECTION PARAMETERS:
export RPC_HOST=thingsboard.cloud
export RPC_PORT=9090
export INTEGRATION_ROUTING_KEY=b75**************************34d
export INTEGRATION_SECRET=vna**************mik
```

Execute the following command to start Klyff:

```bash
sudo service tb-opc-ua-integration start
```
{: .copy-code}

 - **Advanced configuration**

Once can lookup additional configuration parameters inside the yml configuration file.

Open the file for editing using the following command:

```bash 
sudo nano /etc/tb-opc-ua-integration/conf/tb-opc-ua-integration.conf
``` 
{: .copy-code} 

After executing this command you can open logs which are located here `/var/log/tb-opc-ua-integration/`. 
You should see some INFO log messages with your latest Integration configuration that arrived from the server.

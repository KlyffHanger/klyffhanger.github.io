---
layout: docwithnav-pe-edge
title: Installing Klyff Edge on CentOS/RHEL Server
description: Installing Klyff Edge on CentOS/RHEL Server
---

* TOC
{:toc}

{% include templates/edge/install/compatibility-warning-general.md %}

{% assign docsPrefix = "pe/edge/" %}

This guide describes how to install Klyff Edge on RHEL/CentOS 7/8.

{% include templates/edge/install/prerequisites.md %}

## Guided Installation Using Klyff Server Pre-configured Instructions

{% include templates/edge/install/tb-server-pre-configured-install-instructions.md %}

{% include templates/edge/install/manual-install-instructions-intro.md %}

### Pre-installation step 
Before continue to installation execute the following commands in order to install necessary tools:

```bash
sudo yum install -y nano wget
sudo yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

### Step 1. Install Java 17 (OpenJDK) 

{% include templates/install/rhel-java-install.md %}

### Step 2. Configure PostgreSQL

{% include templates/edge/install/rhel-db-postgresql.md %}

### Step 3. Klyff Edge service installation

Download installation package.

```bash
wget https://dist.thingsboard.io/tb-edge-{{ site.release.pe_edge_ver }}.rpm
```
{: .copy-code}

Go to the download repository and install Klyff Edge service

```bash
sudo rpm -Uvh tb-edge-{{ site.release.pe_edge_ver }}.rpm
```
{: .copy-code}


### Step 4. Configure Klyff Edge

{% include templates/edge/install/linux-configure-edge.md %}

### Step 5. Run installation script

{% include templates/edge/install/run-edge-install.md %} 

### Step 6. Restart Klyff Edge service

```bash
sudo service tb-edge restart
```

### Step 7. Open Klyff Edge UI

{% include templates/edge/install/open-edge-ui.md %} 

## Troubleshooting

Klyff Edge logs are stored in the following directory:
 
```bash
/var/log/tb-edge
```

You can issue the following command in order to check if there are any errors on the service side:
 
```bash
cat /var/log/tb-edge/tb-edge.log | grep ERROR
```

{% include templates/edge/install/edge-service-commands.md %} 

## Next Steps

{% include templates/edge/install/next-steps.md %}
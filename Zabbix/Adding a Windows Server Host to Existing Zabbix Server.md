# Zabbix Monitoring Setup Guide

## Adding a Windows Server Host to Existing Zabbix Server

## 1. Overview

This document explains how to add a new Windows Server machine into an existing Zabbix monitoring environment.

### Existing Environment

| Component     | Status                        |
| ------------- | ----------------------------- |
| Zabbix Server | Already installed and running |
| Zabbix Web UI | Available                     |
| Database      | Already configured            |
| New Host      | Windows Server                |

The Windows Server will be monitored using **Zabbix Agent 2**.

---

# 2. Requirements

Before starting, collect the following information:

### Zabbix Server

Example:

```
Hostname: zabbix-server
IP Address: 192.168.1.10
Version: Zabbix 7.4.7
```

### Windows Server

Example:

```
Hostname: WIN-SERVER01
IP Address: 192.168.1.50
Operating System: Windows Server 2022
```

### Network Requirement

Communication:

```
Zabbix Server  ---> Windows Server

Port:
10050/TCP
```

Allow TCP port 10050 through the Windows firewall.

---

# 3. Install Zabbix Agent 2 on Windows Server

## Step 1: Download Agent

Download Zabbix Agent 2 for Windows from:

```
https://www.zabbix.com/download_agents
```

Download:

```
Zabbix Agent 2 MSI package
```

---

## Step 2: Install Agent

Run the MSI installer.

Enter the following information:

|Parameter|Example|
|---|---|
|Server|192.168.1.10|
|ServerActive|192.168.1.10|
|Hostname|WIN-SERVER01|

Example configuration:

```
Server=192.168.1.10
ServerActive=192.168.1.10
Hostname=WIN-SERVER01
```

Complete the installation.

---

# 4. Verify Zabbix Agent Service

Open:

```
services.msc
```

Check:

```
Zabbix Agent 2
```

Status:

```
Running
```

---

# 5. Add Windows Server in Zabbix Web UI

Login to Zabbix:

```
https://zabbix-server-address
```

Go to:

```
Data collection
        |
        Hosts
        |
        Create Host
```

---

## Host Configuration

### Host Name

Enter the same hostname configured in the agent.

Example:

```
WIN-SERVER01
```

---

### Host Groups

Select:

```
Windows servers
```

or create a new group:

```
Production Servers
```

---

### Agent Interface

Add:

```
Type:
Agent

IP Address:
192.168.1.50

Port:
10050
```

---

# 6. Link Windows Monitoring Template

Open:

```
Templates
```

Click:

```
Select
```

Choose:

```
Windows by Zabbix agent
```

Click:

```
Add
```

Save the host.

---

# 7. Verify Host Communication

Go to:

```
Monitoring
      |
      Hosts
```

Check the host status.

Expected:

```
ZBX icon = Green
```

Meaning:

```
Zabbix Server can communicate with Agent
```

---

# 8. Verify Monitoring Data

Go to:

```
Monitoring
       |
       Latest Data
```

Select:

```
WIN-SERVER01
```

Expected monitoring items:

- CPU utilization
- Memory utilization
- Disk space
- Network traffic
- System uptime
- Windows services

---

# 9. Create Dashboard Widgets

Open:

```
Monitoring
       |
       Dashboards
```

Add widgets.

Recommended widgets:

|Widget|Type|Item|
|---|---|---|
|Host Status|Host card|Windows server|
|Problems|Problems|Server alerts|
|CPU Usage|Gauge|CPU utilization|
|Memory Usage|Gauge|Memory utilization|
|Disk Usage|Gauge|Disk used %|
|CPU History|Graph|CPU utilization|
|Memory History|Graph|Memory utilization|
|Network Traffic|Graph|Network traffic|

---

# 10. Monitoring Result

After successful configuration, Zabbix will monitor:

## Operating System

- CPU
- Memory
- Disk
- Network
- Processes
- Services
- Availability

## Example Architecture

```
                 Zabbix Server
              IP: 192.168.1.10
                     |
                     |
                TCP Port 10050
                     |
                     |
          Windows Server / Veeam Server
              IP: 192.168.1.50

              Zabbix Agent 2
```

---

# 11. Troubleshooting

## Host shows Red/Unavailable

Check:

1. Agent service running:

```
services.msc
```

2. Firewall:

```
TCP 10050 allowed
```

3. Agent configuration:

```
Server=<Zabbix Server IP>
Hostname=<Exact Host Name>
```

---

## No Data in Latest Data

Check:

- Template is linked
- Host name matches agent hostname
- Agent service is running
- Network connectivity is available

---

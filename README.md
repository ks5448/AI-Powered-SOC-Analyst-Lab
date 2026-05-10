# AI-Powered SOC Analyst Home Lab

## Overview

This project demonstrates the creation of an AI-assisted SOC (Security Operations Center) analyst workflow using Kali Linux, Ubuntu Server, Python automation, packet capture analysis, and Airia AI integration.

The lab simulates suspicious ICMP traffic between virtual machines in a controlled environment. Network traffic is captured using Tshark, analyzed with Python, converted into structured alert data, and forwarded to an AI pipeline for automated investigation and triage.

---

# Objectives

- Build a beginner-friendly SOC analyst home lab
- Capture live network traffic using Tshark
- Simulate suspicious ICMP traffic between systems
- Automate packet analysis using Python
- Detect abnormal network activity using thresholds
- Generate structured JSON alerts
- Integrate alerts with Airia AI for automated SOC analysis
- Gain hands-on experience with network monitoring and detection workflows

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Kali Linux | SOC analyst workstation / packet capture |
| Ubuntu Server | Traffic generation target |
| Python | Automation and alert generation |
| Tshark | Packet capture and PCAP processing |
| VirtualBox | Lab virtualization |
| Airia AI | AI-powered SOC analysis |
| JSON | Alert formatting |
| CSV | Traffic parsing and analysis |

---

# Lab Architecture

```text
+-------------------+                     +-------------------+
|   Ubuntu Server   | ---- ICMP Ping ---> |    Kali Linux     |
|  Traffic Source   |                     | SOC Analyst VM    |
+-------------------+                     +-------------------+
                                                    |
                                                    v
                                           +------------------+
                                           | Python Analyzer  |
                                           | + Tshark         |
                                           +------------------+
                                                    |
                                                    v
                                           +------------------+
                                           |  Alert JSON      |
                                           +------------------+
                                                    |
                                                    v
                                           +------------------+
                                           |    Airia AI      |
                                           | AI Investigation |
                                           +------------------+
```

---

# Environment Setup

## Virtual Machines

### Kali Linux
- Used as the SOC analyst workstation
- Ran Tshark packet captures
- Executed Python automation scripts
- Sent alerts to Airia AI

### Ubuntu Server
- Used as the traffic-generating host
- Simulated ICMP traffic using ping

---

# Network Configuration

Both VMs were configured on the same VirtualBox network to allow communication between systems.

Example communication flow:

```bash
Ubuntu VM ---> ping ---> Kali VM
```

---

# Packet Capture Process

Traffic was captured using Tshark on the Kali Linux VM.

Example command:

```bash
sudo tshark -i eth0 -f "icmp" -w traffic.pcap
```

The PCAP file was then processed automatically by the Python script.

---

# Python SOC Automation Workflow

The Python script automated the following tasks:

1. Start packet capture
2. Save traffic into a PCAP file
3. Convert PCAP data into CSV format
4. Analyze packet counts by source IP
5. Detect suspicious traffic volumes
6. Generate structured JSON alerts
7. Send alerts to Airia AI for investigation

---

# Detection Logic

The script monitored packet volume from source IP addresses.

If packet counts exceeded a configured threshold, the activity was flagged as suspicious.

Example:

```python
THRESHOLD = 40
```

Suspicious activity generated an alert similar to:

```json
{
  "alert_type": "Suspicious Network Volume",
  "indicator_value": "192.168.x.x",
  "packet_count": 85
}
```

---

# Airia AI Integration

Generated alerts were forwarded to Airia AI using API requests.

The AI pipeline analyzed:
- Source IP activity
- Traffic volume
- Potential scanning behavior
- Suspicious network patterns

This simulated a real-world SOC workflow where alerts are enriched and triaged automatically.

---

# Skills Demonstrated

- Network traffic analysis
- Packet capture using Tshark
- PCAP analysis
- Python automation
- SOC alert triage workflows
- Threat detection logic
- JSON data handling
- API integration
- Linux administration
- Cybersecurity home lab development

---

# Future Improvements

- Add TCP/UDP detection capabilities
- Integrate Sigma detection rules
- Forward alerts into a SIEM platform
- Add Suricata or Zeek integration
- Build a real-time dashboard
- Implement threat intelligence enrichment
- Add email or Discord alerting

---

# Disclaimer

This project was built strictly for educational and defensive cybersecurity purposes within a controlled lab environment.

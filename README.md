# -NETWORKWALKS-IRFAN-RS-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP

## Virtual Cybersecurity Lab Deployment & Network Infrastructure Setup

<div align="center">

**Building a secure, isolated and recoverable environment for ethical hacking and cybersecurity research.**

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red?style=for-the-badge)
![Kali Linux](https://img.shields.io/badge/OS-Kali%20Linux-blue?style=for-the-badge&logo=kalilinux)
![VirtualBox](https://img.shields.io/badge/Platform-VirtualBox-darkblue?style=for-the-badge&logo=virtualbox)
![NetworkWalks](https://img.shields.io/badge/Program-NetworkWalks-black?style=for-the-badge)

</div>

---

## 📌 01. Project Overview

This Project is a virtual cybersecurity laboratory designed to provide a controlled environment for learning ethical hacking, network security and penetration testing.

The laboratory uses Oracle VirtualBox as its virtualization platform and Kali Linux as its primary security-testing operating system.

Instead of performing security experiments directly on a personal or production system, this project establishes a dedicated virtual environment where different security tools and networking concepts can be explored safely.

The environment is also designed to support additional virtual machines in future exercises.

## 🎯 02. Project Objectives

- Deploy a Kali Linux virtual machine.
- Configure a dedicated virtual network.
- Understand virtual network communication.
- Configure IPv4 addressing and DNS.
- Verify network and internet connectivity.
- Establish a recoverable VM baseline using snapshots.
- Document the installation and configuration process.
- Prepare an environment for future penetration-testing exercises.

## 🏗️ 03. Laboratory Architecture

The proposed architecture separates the host operating system from the virtual cybersecurity environment.

```text
                 HOST MACHINE
                Windows OS
                     |
              Oracle VirtualBox
                     |
               NAT Network
                     |
          Private Lab Network
                     |
          +----------+----------+
          |                     |
      Kali Linux           Future Target
      Attacker VM            VM
          |                     |
          +----------+----------+
                     |
             Lab Communication
```

**Architecture explanation:**

- Host Machine: Physical computer running the virtualization software.
- VirtualBox: Manages the virtual machines and their network connections.
- NAT Network: Provides connectivity between participating VMs and outbound network access.
- Kali Linux: Primary environment for security testing.
- Target VM: Reserved for future authorized testing exercises.

## ⚙️ 04. Technology Stack

| Component | Technology |
|---|---|
| Host Operating System | Windows |
| Virtualization | Oracle VirtualBox |
| Security Distribution | Kali Linux |
| Archive Utility | 7-Zip |
| Network Configuration | IPv4 |
| Virtual Network | NAT Network |
| Network Testing | Ping, IP tools |
| Security Tools | Nmap, Wireshark |
| Documentation | Markdown, GitHub |

## 🌐 05. Network Configuration


| Parameter | Example |
|---|---|
| Network Mode | NAT Network |
| Network Name | Sentinel-Lab |
| Network Address | 10.10.10.0/24 |
| Kali IP | 10.10.10.10 |
| Default Gateway | 10.10.10.1 |
| DNS Server | 8.8.8.8 |
| Future VM Range | 10.10.10.11–10.10.10.99 |

**Why NAT Network?**

A NAT Network allows multiple connected virtual machines to communicate with each other while supporting outbound network connectivity.

This makes it useful for building a multi-machine testing environment.

Note: The example addressing scheme must be checked against the actual VirtualBox network configuration before use.

## 🪜 06. Implementation Workflow

### Step 1 – Prepare the Environment

- Download and install 7-Zip.
- Download Oracle VirtualBox.
- Download the Kali Linux virtual machine image from its official website.
- Verify the downloaded image where applicable.

### Step 2 – Configure VirtualBox

Install VirtualBox and check that hardware virtualization is enabled.

Prepare the virtualization environment for importing the Kali Linux machine.

### Step 3 – Create a Dedicated Virtual Network

Create a NAT Network named `Sentinel-Lab`.

Configure the IPv4 network prefix and DHCP settings according to the lab requirements.

### Step 4 – Deploy Kali Linux

Import the Kali Linux virtual machine into VirtualBox.

Allocate suitable system resources and attach its network adapter to the dedicated NAT Network.

### Step 5 – Configure Network Settings

Inspect the network interfaces and configure the appropriate IPv4 settings.

Useful commands:

```bash
ip a
ip route
ip link
```

Check the network connection and DNS configuration.

### Step 6 – Establish a Recovery Point

After the initial setup is verified, create a VirtualBox snapshot named:

`Sentinel-Clean-Baseline`

This provides a recovery point before future security experiments.

## 🔍 07. Verification & Testing

The following tests are used to validate the environment.

| Test | Command | Purpose |
|---|---|---|
| IP Verification | `ip a` | Inspect IP configuration |
| Routing | `ip route` | Check routing table |
| Gateway | `ping <gateway>` | Test gateway connectivity |
| Internet | `ping 8.8.8.8` | Test outbound connectivity |
| DNS | `nslookup example.com` | Verify DNS resolution |
| Nmap | `nmap --version` | Check tool installation |

**Test results:**

Record the actual output and status after executing each test.

- [ ] IP configuration verified
- [ ] Default gateway reachable
- [ ] Internet connectivity verified
- [ ] DNS resolution successful
- [ ] Nmap installation verified
- [ ] Snapshot created

## 🐞 08. Troubleshooting & Resolution

Document real problems encountered during implementation.

### Issue 1 – Virtual Machine Fails to Start

**Possible cause:** Hardware virtualization is disabled.

**Resolution:**
1. Restart the computer.
2. Enter BIOS/UEFI settings.
3. Enable Intel VT-x or AMD-V where supported.
4. Save changes and restart.
5. Try launching the virtual machine again.

### Issue 2 – Kali Linux Has No Internet Connection

**Possible causes:**
- Incorrect network adapter configuration.
- Incorrect gateway settings.
- DNS configuration problems.
- Network service issues.

**Troubleshooting commands:**

```bash
ip a
ip route
nmcli device status
nmcli connection show
```

Check the adapter mode in VirtualBox and verify the connection settings before making changes.

### Issue 3 – Incorrect IP Configuration

Inspect the active network interface and verify its IPv4 address, subnet mask and gateway.

Do not assume that every system uses the same interface or connection name.

## 🧠 09. Key Learning Outcomes

Through this project, I aim to develop practical understanding of:

**Virtualization:** Deploying and managing isolated operating systems.

**Networking:** Understanding NAT Network, IP addressing, routing and DNS.

**Linux Administration:** Working with Kali Linux and essential terminal commands.

**Cybersecurity Infrastructure:** Preparing a dedicated environment for authorized security testing.

**System Recovery:** Using virtual machine snapshots to maintain a clean baseline.

**Technical Documentation:** Recording configurations, test results and troubleshooting solutions.

## 🔮 10. Future Scope

The laboratory can be expanded with:

- A vulnerable target machine for authorized testing.
- Network reconnaissance using Nmap.
- Packet inspection using Wireshark.
- Vulnerability assessment exercises.
- Web application security testing.
- Network traffic monitoring and analysis.

## 🔐 11. Ethical Use & Disclaimer

This project is developed strictly for educational and cybersecurity research purposes.

All testing must be performed on personally owned systems, isolated lab machines or systems for which explicit authorization has been obtained.

Unauthorized access, scanning or exploitation of external systems is not permitted.

## 📚 12. References & Resources

- Kali Linux: https://www.kali.org/get-kali/
- Oracle VirtualBox: https://www.virtualbox.org/wiki/Downloads
- 7-Zip: https://www.7-zip.org/
- Nmap: https://nmap.org/
- Wireshark: https://www.wireshark.org/

## 👨‍💻 13. Project Information

**Project:** Virtual Cybersecurity Lab Deployment

**Program:** NetworkWalks Cybersecurity Program

**Week:** 01

**Category:** Cybersecurity / Linux / Networking / Virtualization

**Author:** Irfan

---

<div align="center">

**PROJECT SENTINEL | BUILD • TEST • LEARN • SECURE**

*Developing practical cybersecurity skills through hands-on laboratory exercises.*

</div>
### BUILD • EXPLORE • SECURE

*Learning cybersecurity through practical implementation.*

\</div>

# 🔥 FortiGate LAN to DMZ Network Lab

## 📌 Overview

This lab demonstrates a basic network architecture using a FortiGate firewall to control traffic between a LAN and a DMZ network.

The goal is to understand:

* Network segmentation (LAN vs DMZ)
* Firewall policies configuration
* Routing between different subnets

---

## 🖼️ Topology

![Topology](topology.png)

---

## 🌐 Network Design

### 🔹 LAN Network

* Subnet: 10.1.1.0/24
* Connected to FortiGate (port2)
* Represents internal trusted network

### 🔹 DMZ Network

* Subnet: 172.16.10.0/24
* Connected to FortiGate (port3 via Switch)
* Contains external-facing devices (simulated routers)

### 🔹 WAN Network

* Used for internet simulation (optional)

---

## 🧱 Devices Used

* FortiGate Firewall
* Cisco Routers
* Layer 2 Switch (for DMZ connectivity)

---

## ⚙️ Configuration Details

### 🔸 FortiGate

* port2 → LAN (10.1.1.1/24)
* port3 → DMZ (172.16.10.1/24)
* Firewall Policy:

  * Source: LAN
  * Destination: DMZ
  * Action: ACCEPT
  * NAT: Disabled

---

### 🔸 Routers (LAN Side)

* IP Address: 10.1.1.10/24
* Default Gateway: 10.1.1.1

---

### 🔸 Routers (DMZ Side)

* IP Addresses:

  * 172.16.10.2/24
  * 172.16.10.3/24
* Static Route:

  * Destination: 10.1.1.0/24
  * Next Hop: 172.16.10.1

---

### 🔸 Switch

* Layer 2 device
* Used to connect multiple devices in DMZ
* No IP configuration required

---

## 🔐 Security Concept

The FortiGate firewall controls traffic between zones:

* ✅ LAN → DMZ allowed
* ❌ DMZ → LAN denied (by default)

This ensures:

* Internal network protection
* Controlled access to DMZ resources

---

## 🧪 Testing

From LAN Router:

```bash
ping 172.16.10.2
ping 172.16.10.3
```

Expected result:

* Successful communication via FortiGate firewall

---

## 🎯 Key Learnings

* Difference between LAN and DMZ
* Role of firewall policies
* Importance of network segmentation
* Basic routing configuration

---

## 🚀 Future Improvements

* Add Internet access (WAN + NAT)
* Configure DMZ Web Server
* Implement WAN → DMZ access (VIP / Port Forwarding)
* Add security profiles (IPS, Antivirus)

---

## 👨‍💻 Author

Soufiane Ajili
Network & Systems Engineer (aspiring)

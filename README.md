# 🚀 CCNA Lab 3 – Multi-Floor Network Design with OSPF, VLAN, and Security

## 📌 Overview

This lab focuses on designing a multi-floor enterprise network with proper segmentation, dynamic routing, and basic security features.

The network includes multiple VLANs across floors, inter-VLAN routing, and dynamic routing using OSPF. Additional features like DHCP, SSH, and port security are also implemented.

---

## 🧠 Problem Statement

In a multi-floor organization:

* Different departments need to be separated for security
* Manual routing becomes complex as the network grows
* Unauthorized access to switch ports can cause security issues

Solution:

* Use VLANs for segmentation
* Use OSPF for dynamic routing
* Apply security features like SSH and port security

---

## 🎯 Objective

* Create VLANs for multiple departments
* Enable inter-VLAN routing
* Connect multiple routers between floors
* Configure OSPF for automatic route exchange
* Implement DHCP for IP assignment
* Enable secure remote access using SSH
* Apply port security on switch ports

---

## 🌐 Network Design

Example VLAN allocation:

| VLAN | Department | Network        |
| ---- | ---------- | -------------- |
| 10   | IT         | 192.168.1.0/26 |
| 20   | Admin      | 192.168.2.0/26 |
| 30   | HR         | 192.168.3.0/26 |
| 40   | Finance    | 192.168.4.0/26 |
| 50   | Sales      | 192.168.5.0/26 |
| 60   | Reception  | 192.168.6.0/26 |
| 70   | Store      | 192.168.7.0/26 |
| 80   | Logistics  | 192.168.8.0/26 |

---

## ⚙️ How It Works (Concept Explanation)

### 🔹 VLAN + Inter-VLAN Routing

* VLANs separate departments
* Router or L3 switch allows communication

### 🔹 OSPF (Open Shortest Path First)

* Dynamic routing protocol
* Automatically shares routes between routers
* Faster and scalable compared to static routing

### 🔹 DHCP

* Automatically assigns IP addresses

### 🔹 SSH

* Secure remote access to network devices

### 🔹 Port Security

* Restricts unauthorized devices on switch ports

---

## 💻 Configuration Commands

---

### 🔹 VLAN Configuration (Switch)

```id="q2k8p5"
enable
configure terminal

vlan 10
vlan 20
vlan 30
vlan 40
vlan 50
vlan 60
vlan 70
vlan 80
```

---

### 🔹 Port Assignment

```id="x9v4m2"
interface range fa0/1 - 4
switchport mode access
switchport access vlan 10
```

(Repeat for other VLANs as needed)

---

### 🔹 Trunk Configuration

```id="w6t3r8"
interface fa0/24
switchport mode trunk
```

---

### 🔹 Router / L3 Routing

```id="d7f2k1"
ip routing
```

---

### 🔹 OSPF Configuration

```id="z5n8b3"
router ospf 1
network 192.168.0.0 0.0.255.255 area 0
```

---

### 🔹 DHCP Configuration

```id="c1m7q4"
ip dhcp pool VLAN10
network 192.168.1.0 255.255.255.192
default-router 192.168.1.1
```

---

### 🔹 SSH Configuration

```id="p8v2s6"
hostname R1
ip domain-name lab.local
username admin secret Cisco@123

crypto key generate rsa
1024

ip ssh version 2

line vty 0 4
login local
transport input ssh
```

---

### 🔹 Port Security

```id="y3k9f7"
interface fa0/1
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security mac-address sticky
```

---

## 🔍 Verification Commands

```id="n4t8w2"
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show ip ospf neighbor
show ip dhcp binding
show port-security
```

---

## 📊 Result

✅ VLANs successfully created and working
✅ Inter-VLAN communication enabled
✅ OSPF routes exchanged dynamically
✅ DHCP assigning IP addresses
✅ SSH working for remote login
✅ Port security restricting unauthorized devices

---

## ⚠️ Issues Faced & Solution

### ❌ Issue:

* OSPF neighbors not forming

### 🔍 Cause:

* Incorrect network statement

### ✅ Fix:

* Corrected OSPF network configuration

---

### ❌ Issue:

* VLAN communication failure

### 🔍 Cause:

* Trunk misconfiguration

### ✅ Fix:

* Enabled trunk port correctly

---

## 💡 Key Learnings

* Importance of VLAN segmentation
* How dynamic routing simplifies large networks
* Role of security in enterprise networks
* Practical understanding of OSPF

---

## 🎯 Real-World Use Case

* Multi-floor office networks
* Enterprise campus networks
* Secure segmented network environments

---

## 🚀 Conclusion

This lab demonstrates how enterprise networks are built using segmentation, dynamic routing, and security. It provides hands-on experience with real-world networking concepts essential for a network engineer role.

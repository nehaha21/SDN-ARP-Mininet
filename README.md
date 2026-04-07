# ARP Handling in SDN Networks using Mininet and POX

## Objective

To implement and demonstrate ARP handling in a Software Defined Network (SDN) using Mininet and a POX controller.

---

## Tools Used

* Ubuntu Virtual Machine
* Mininet
* POX Controller
* Open vSwitch
* OpenFlow 1.0

---

## Topology

* 1 Switch (s1)
* 2 Hosts (h1, h2)
* 1 Remote Controller (c0)

---

## Controller Description

The controller is implemented using POX. It listens for PacketIn events from the switch and:

* Identifies ARP requests
* Logs ARP traffic
* Floods ARP packets so the destination host can respond
* Floods other packets (like ICMP) to ensure communication between hosts

---

## Steps to Run

### 1. Run Controller

```bash
cd ~/pox
python3 pox.py openflow.of_01 arp_controller
```

---

### 2. Run Mininet

```bash
sudo mn -c
sudo mn --topo single,2 --mac --controller=remote,ip=127.0.0.1,port=6633 --switch ovsk,protocols=OpenFlow10
```

---

### 3. Test Connectivity

Inside Mininet:

```bash
h1 ping -c 1 h2
pingall
```

---

## Verification

The following commands were used to verify the setup:

```bash
nodes
net
dump
```

### Expected Output

* Successful ping between h1 and h2
* `0% packet loss`
* Both hosts reachable

---

## Results

* Controller successfully handled ARP traffic
* Hosts communicated successfully through the SDN controller
* Network topology was verified using Mininet commands

---

## Conclusion

This project demonstrates how ARP handling can be managed in an SDN environment using a centralized controller. The POX controller processes packet events and enables communication between hosts in a Mininet-based network.

---

## Repository Contents

* `arp_controller.py` → Controller code
* `README.md` → Project documentation
* Screenshots → Output verification

---

## Author

Neha Rastogi

# Virtual Networks Lab using Linux and the CORE Network Emulator

# Lab 3: OSPF Performance 

Each of the following sections describes an experiment based on the network topology provided by the  **[Project_OSPF_TCP.imn](https://github.com/kelsayed/CoreNetLab/NetTopo/Project_OSPF_TCP.imn)**  file. In your report, divide the answers to correspond to one of these sections in exactly the same sequence and same name, for example use Question 2.1, Question 3.2 and so on.

The [Introductory Lab](https://github.com/kelsayed/CoreNetLab/IntroLab.md) explained and introduced most of the needed tools like iperf3, vtysh, wireshark, etc. If you have not gone through it, do not start working on the assignment below.

It is better to start the network emulation once and run Wireshark captures. You can reset Wireshark captures from experiment to another.

## 1) OSPF Link Cost Changes

1. Stop any running iperf3 clients.

2. Set all links to have zero loss in the two directions with 100 Mbps speed.

3. Run iperf3 between n7 and n11 for a duration of 500 seconds or longer. Identify the path between n7 and n11.

4. Open vtysh on node n5 by opening a bash terminal and typing vtysh. Now we can configure router and link costs.

5. Type the following in vtysh:
   `show ip ospf interface eth1`
   This displays information about interface eth1. Note its ospf cost.

6. Type the following
   `configure terminal`

   `interface eth1` (the interface for the link between n5 and n4)
   `ospf cost 40` (set cost to 40)

### **Questions**

1. Check what happens to the path between n7 and n11 (as seen after steps 3 and 6)? Explain what happens.
2. Set the cost of eth1 at node n5 back to 10. Establish two iperf3 connections: one from n7 to n11 and the second from n11 to n7 both for duration of 500 seconds. Now go to node n4 and set interface cost for interface connecting n4 with n5 to 40.
    What happens in the paths of the two connections? Explain what happens. What do you conclude?

## 2) OSPF Database Updates

1. Start wireshark and have its filter to capture only OSPF related packets.

2. Go to another router say router n2, open vtysh and issue the commands:
   `config terminal`
   `show ip ospf database`
   `show ip ospf route`

3. On router n4, set link cost of eth1 to 20. Capture the link state packets advertised in Wireshark.

4. Go to router n4, go out of vtysh, or open new bash terminal and issue the following commands to disconnect router n4 from the network:

   `ifconfig eth0 down`
   `ifconfig eth1 down`
   `ifconfig eth2 down`

### Questions

1. Capture and explain the outputs due to execution of step 2. Why some destinations have more than route in the routing tables?
2. After executing step 3, determine how long it took the network to exchange link state packets and adjust routing tables. **(Hint: you can calculate the required time by observing the time of first OSPF update message and the last ACK from Wireshark).**
3. After execution of step 4, identify the new routing table and router database at router n2. Explain the updates in the new routing table and the new database.

## 3)OSPF Link State Advertisement Periodicity

This part is on your own. No instructions are given. Stop any previous iperf3 connections. Let Wireshark capture focus on Ospfv2 only (IPv4).

Apply the filter (ospf.msg.lsupdate \|\| ospf.msg.lsack) && ip.addr == 224.0.0.5

### Questions

1. Bring router n4 down (assuming it is currently up) and then up again and determine how long it took the network to recognize the router is down/up.

2. Now, the following is a bonus question (extra marks).

   Explain the noticed behavior of the link state update packet storms (flooding) where it generally takes longer times for the LSP exchange to die out (i.e. LSP exchange stops) when a router is down as compared with the case when the router is up again.
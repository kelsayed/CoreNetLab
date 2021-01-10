# Virtual Networks Lab using Linux and the CORE Network Emulator

# Lab 2: TCP Performance 

Each of the following sections describes an experiment based on the network topology provided by the  **[Project_OSPF_TCP.imn](https://github.com/kelsayed/CoreNetLab/NetTopo/Project_OSPF_TCP.imn)**  file. In your report, divide the answers to correspond to one of these sections in exactly the same sequence and same name, for example use Question 2.1, Question 3.2 and so on.

The [Introductory Lab](https://github.com/kelsayed/CoreNetLab/IntroLab.md) explained and introduced most of the needed tools like iperf3, vtysh, wireshark, etc. If you have not gone through it, do not start working on the assignment below.

It is better to start the network emulation once and run Wireshark captures. You can reset Wireshark captures from experiment to another.

## 1) Effect of TCP Window Size 

1.  Set wireshark filter to display TCP packets only.

2.  Start an iperf3 server on node n11.

3.  Start an iperf3 client on node n7 connecting to server on node n11 for a duration of 40 seconds and reporting interval of 10. **Note that in iperf, the client is the node sending the traffic and the server simply receives and sends an ACK**.

### **Questions**

1. Vary iperf3 window size from 1Kbytes to 6 Kbytes in increments of 1 Kbyte, then set it to 12, 16, 24, 32 Kbytes. Plot the average throughput and the average number of retransmissions as function of window size. Comment on the results and explain the zigzag behaviour noticed for larger window sizes. Note that number of retransmissions is the 5th column in iperf3 default output.

2. Click on any of the TCP a data segment whose source is node n7, dissect the segment by following different protocol layer headers from TCP-\>IP-\>Ethernet identifying how many header bytes are added by each layer, identify the TCP options used.

3. Repeat for an ACK packet sent from node n11.


## 2) TCP short versus long paths

1.  Run an iperf3 server on node n8.

2.  Start an iperf3 client on node n7 connecting to server on node n8 for a duration of 40 seconds and reporting interval of 10 with window size 4K.

### **Questions**

1. Compare the result of throughput with the case when connection was made to node n11. Why throughput drops when connecting to n8 although capacities on the two paths are the same.

## 3) Higher Link Capacity with Drops versus Reliable Lower Capacity

This questions for this part are based on the path between n7 and n11.

For each case of the following, run iperf3 client from n7 to n11 with window size 4K.

a. Select link between n4 and n5, configure it to have capacity of 10 Mbps with zero loss in both directions.

b. Select link between n4 and n5, configure it to have capacity of 3 Mbps with zero loss in both directions.

c. Select link between n4 and n5, configure it to have capacity of 10 Mbps with 5% loss in both directions.

d. Select link between n4 and n5, configure it to have capacity of 100 Mbps with 10% loss in both directions.

e. Select link between n4 and n5, configure it to have capacity of 10 Mbps with 1% loss in direction from n4 to n5 and 0% loss in the other direction.

f. Select link between n4 and n5, configure it to have capacity of 10 Mbps with 0% loss in direction from n4 to n5 and 1% loss in the other direction.

### **Questions**

1. Compare throughputs in cases a, b, c. Why b is better than c?

2. Compare throughputs in cases b, c and d. Which is better? Why?

3. Compare throughputs in cases e and f? Which is better? Why?




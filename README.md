# dscp-remarking
https://github.com/caophuonghuy/dscp-remarking

Tools to test dscp marking, remarking with ixia-c-one.

Here is simple topology

ixia-c-one(eth-1)-------(eth-1/1)DUT(eth-1/2)-------(eth-2)ixia-c-one

Besides the ixia-c-one and Device Under Test (DUT), there is also an ixia client container named ixia-c-client. The client will create 1 source host on eth-1 and one destination host on eth-2 of the ixia-c-one and send a number of IP packets from source host to destination host with a specific dscp value that you can assign. After sending, client will capture the packet received on destination host and examinate the dscp value which may have been marked/ remarked on the way.

Access the client by command:

#docker exec -it ixia-c-client sh

then run the client tool

#./dscp_test_tool

Enter the configuration of client (IP address, gateway, number of ip packet, dscp value in ip packets) and see the result.

In this topo, the DUT is a 7220 IXR-D2L container which will remark ip packet with dscp 46 to dscp 40. The DUT can be replace by another box or a network for more complicated setup.


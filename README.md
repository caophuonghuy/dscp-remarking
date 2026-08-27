# dscp-remarking

Tools to test qos marking, remarking with ixia-c-one.

Here is simple topology

ixia-c-one(eth-1)-------(eth-1/1)DUT(eth-1/2)-------(eth-2)ixia-c-one

In the lab, there is also an ixia client container named ixia-c-client. The client will create 1 source host on eth-1 and one destination host on eth-2 of the ixia-c-one and send a number of IP packets from source host to destination host with a specific dscp value that you can assign. After sending, client will capture the packet received on destination host and examinate the dscp value which may have been marked/ remarked on the way.

To deploy the lab:

#git clone https://github.com/caophuonghuy/dscp-remarking

#cd dscp-remarking/

#clab deploy -t qos-marking.yaml

Access the client by command:

#docker exec -it ixia-c-client sh

then run the client tool

#./marking_test_tool

Enter the configuration of client (IP address, gateway, VLAN, dot1p, number of ip packet, dscp value in ip packets) and see the result.

(In case you do not have VLAN setup, can use command

#./dscp_test_tool

to do a quick one for just DSCP test with null port in both sides. This is the version 0.1 of this tool)

In this topo, the DUT (device under test) is a 7220 IXR-D2L container which will remark ip packet with dscp 46 to dscp 40. The DUT can be replaced by another box or a network for more complicated setup.

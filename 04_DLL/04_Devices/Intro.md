# Connecting Devices

| Device | Layer | Knowledge |
| :---: | :---: | :---: |
| Passive Hub | Below PL | None |
| Repeater or Hub | PL | Signal |
| Bridge or Layer 2 Switch | DLL + PL | PA + Signal |
| Router or Layer 3 Switch | NL + DLL + PL | LA + PA + Signal |
| Gateway | All 5 Layers | Messages + LA + PA + Signal |

- Gateway is used for Firewalls

## Passive Hub

- It simply act as a connector to connect different wires.
- This type of hub is part of transmission media so it's below physical layer.
- It simply broadcast the signal to all ports except the one from which it received the signal.
- Since it is below physical layer so it can't change(regenerate or Amplify) the signal before broadcasting it.
- No filtering capabilty is there.

## Repeator

- It is a device that operates only on physical layer.
- Repeator must receive signal before it becomes too weak or corrupted & it regenerate the original bit pattern.
- Hence location of repeator in media is very important.
- Repeator is different from amplifier as amplifier can't differentiate b/w signal & noise, hence it amplifies noise also.
- Repeater doesn't amplify the signal, it simply regenerates the signal.
- Repeater is used to extend the length of the network.
- Repeater is for analog as well as digital signal.
- Repeater has two 2 ports, It receives the signal from one port regenrate it & simply forward it from another port.
- Hence, it does not have any filtering capability.
- Repeator is used to connect 2 LAN segments not 2 LANs i.e. it is used to connect 2 segments of same LAN.

## Active Hub
- By default Hub means Active Hub not passive hub.
- It is a multiport repeator.
- It receives the signal from one of the port and after regenerating signal, it broadcast the same from all the ports except incoming port.

## Bridge
- Bridge is a layer-2 device.
- So, it iwll work on both Physical Layer and Data Link Layer.
- As a Physical Layer device, it will regenerate the signal.
- As a Data Link Layer device, it will filter the signal, as it knows the MAC address of all the devices connected to it.
- Every Bridge has a Bridge table, which contains the MAC address of all the devices mapped with the port number which helps to decide through which port packet is to be forwarded.
- If Devices on the same side of port are communicating then the packet which bridge will get it will simply drop it.
  - During this phenomena, all the devices connected to the bridge can communicate to the devices on the same side of port where they are.
  - Hence Bridge is used to connect 2 or more LANs.
- Bridge can read or check Physical Address of Sender and Receiver but it can not change the address.
  - Hence, Bridge cannot connect 2 LANs with different protocols.

## Note:
> All the Devices discussed below will have the functionalities
> - Filtering  
> - Store and Forward Technique
> - No Collision

### Bridge Table
| Physical Address | Port |
| :---: | :---: |
| A8:9B:4B:12:34:56 | 1 |
| 00:1B:44:12:34:56 | 1 |
| 00:1B:44:12:34:57 | 2 |
| 00:1B:44:12:34:58 | 3 |
| FA:9B:4B:12:34:56 | 2 |
- There can be 2 ways to fill this form
  1. Manual Entry
  In this case, the network admininstrator will manually enter the MAC address of all the devices connected to the bridge.  
  This is a very tedious task.
  2. Bridge Automatically
  Those are called Transparent Bridges defined by IEEE 802.1D standard.
    - Bridge must forward frames correctly.
    - Bridge must fill the table automatically by learning process.
    - Loops in the system must be avoided.

- Bridge fills the table automatically by learning process.
  - When a frame arrives at a bridge, the bridge reads the source address of the frame and enters it into the table with the port number on which it arrived.
  - If the destination address of the frame is not in the table, the bridge forwards the frame to all ports except the incoming port.
  - If the destination address of the frame is in the table, the bridge forwards the frame only to the port indicated in the table.
  - If the destination address of the frame is the same as the source address, the bridge drops the frame.
  - If the destination address of the frame is a broadcast address, the bridge forwards the frame to all ports except the incoming port.
  - If the destination address of the frame is a multicast address, the bridge forwards the frame to all ports that are members of the multicast group.
- If there are 2 transparent bridges connected then their are chances of looping.
  - In such cases we remove one of the port of the bridges.
  1. Here we make the minimum spanning tree.
  - Here cost criteria is No. of hops and distance.
    - Bridge to LAN distance is 1 hop.
    - LAN to Bridge distance is 0 hop.
    - Bridge to Bridge distance is 1 hop.
  - Spanning tree protocol is dynamic, meaning that it can change the topology of the network as the network changes or any error occurs.
  - They use Bridge Protocol Data Unit(BPDU) to communicate with each other.
  2. Source Routing Bridges
    - Source in it's header define which bridge will forward the packets.
    - Here every station has bridge table.

## Layer-2 Switch

- It has n ports where n is the no. of devices connected to it.
- In case of Bridge we had n ports to connect n LANs. 
  - What happens in case of Bridge is that all the devices are connected to one port than their bandwidth will be divided.
  - Like 10 devices are there and 5 on each side makes a LAN, then the bandwidth of the LAN will be divided into 6 parts.
  - In case of Switch, every device is connected to different port, hence the bandwidth of the LAN will not be divided.
  - Like 10 devices are their then all those 10 devices are connected to the switch through one seperate port, hence bandwidth of each will just be divided into 2 parts one for itself and one for the switch.
- In case of switch any 2 station want to communicate, their packets go to the switch and switch will forward the packet to the destination port, hence here traffice will be more as compared to bridge.
- Also the buffer size of switch is more as compared to bridge, buffer is used to store other packets received from different sources while processing one packet.
- Both uses Store and Forward technique.
- There will never occur collision.

## Routers

- Router is a layer-3 device.
- It works on Network Layer(IP Address), Data Link Layer(Physical Address Knowledge) and Physical Layer(Regenerate Signal).
- It can read and change the Physical Address as well as Logical Address.
- Connect two LANs with different protocols.
  - Example can connect a Token Ring LAN and Ehternet LAN.
- When we connected LANs using Bridge we can't say we created an Internet, but we will call it a single LAN.
  - Here when we get a broadcast packet it will be forwarded to all the ports except the incoming port.
  - While in case of Internet, it is not forwarded to all the ports else advertising would have been easier.
  - In place of bridge we just replace it with Router, then we can it is a netwrok as now we have eliminated Broadcasting.
- Router filter out broadcast packet.
- To connect LAN with a WAN we use Router.
- Router can do fragmentation like if token ring with MTU = 1000, send packet to Ethernet with MTU = 400, then it will perform fragmentation.
- It also does routing which helps decide which path is best for the packet.

## Layer-3 Switch

- More faster and sophisticated than router.

## Gateway

- To connect 2 networks with different network Model
  - Example to connect TCP/IP network with ATM network.
- Gateway is the only device that knows what data we are sending.
- It is a type of computer which can connect two different networks based on two different models.
- Blocks unwanted messages

## Collision Domain & Broadcast Domain

- Collision Domain is the part of Network in which collision can take place.
- Broadcast Domain is the part of network in which broadcasting can be done.
- In case of Devices like Actice Hub, Repeator or Passive Hub connected devices the whole network is the collision domain. Same for the Broadcast Domain. As both can occur on entire netwrok Domain for both is 1.
- In case of Bridge/ Layer -2 switch, they broadcast the packet to entire network. For the collision domain collision can occur on the side of LAN but never across LAN as discussed Bridges are collision free.
  - $\therefore$ Collision domain for Bridge/Layer2 switch is the number of ports they have.
  - Bridge reduces the Collision Domain. **(GATE QUESTION)**
  - We have written reduces because earlier collision was over entire Network but now only over the part of LANs.
- In case of Router/Layer-3 switch, they filter out the broadcast so Broadcast Domain are jusr the number of ports it has, Same goes for the Colliison Domain.
  - It reduces Broadcast and Collision Domain
  - Both Domains are equal to the number of ports.
- Same as Router for Gateway.
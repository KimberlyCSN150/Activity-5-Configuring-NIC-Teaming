# Activity-5-Configuring-NIC-Teaming

Combining multiple network adapters on the domain controller into a single logical team for fault tolerance and throughput.

Background

NIC Teaming aggregates 1–32 physical NICs into one virtual adapter, providing fault tolerance and better performance. Multiple teams can connect to different VLANs if needed.

Before enabling teaming on a physical switch: configure the connecting switch ports as trunk in promiscuous mode, e.g.:

interface range fa0/1-3
switchport mode trunk

Switch-independent mode note (per Microsoft docs): with address hash or dynamic load distribution, outbound traffic uses the MAC address of the primary team member — the first NIC to bind after team creation or a reboot. Because that can change non-deterministically across reboots, the team's effective MAC address can also change.

Steps

Shut down the domain controller VM and add 2 additional network adapters (attached to the Internal Network)
Boot the domain controller
Open Network Connections to confirm all 3 NICs are visible
Record the MAC address of each adapter (Status → Details)
Adapter 1 MAC: __________
Adapter 2 MAC: __________
Adapter 3 MAC: __________
Enable NIC Teaming from Server Manager
Create a new team, name it Team 1, and include all 3 adapters
Set Load Balancing Mode to Address Hash (Additional Properties)
Note which adapter activated first (becomes the primary)
In Network Connections, confirm the Team NIC's MAC address matches the primary adapter
Log off

Question to answer:

Which adapter became the primary, and does the Team NIC's MAC address confirm it?

<img width="975" height="1094" alt="image" src="https://github.com/user-attachments/assets/aa5c1092-33e2-4202-9967-617122390828" />

<img width="975" height="1036" alt="image" src="https://github.com/user-attachments/assets/dd764386-0db2-4737-8840-e9deec008ace" />




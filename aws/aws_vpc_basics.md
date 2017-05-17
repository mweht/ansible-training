<h2>AWS VPC (Virtual Private Cloud)</h2>

<h4> VPC Essentials </h4>

Amazon Virtual Private Cloud enables you to launch AWS resources into a virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own datacenter, with the benefits of using the scalable infrastructure of AWS.

**A VPC is designed to resemble:**
- Private on premise data centers
- Private corporate networks

**Private network features available in AWS VPCs:**
- Private and public subnets
- Scalable architecture
- Ability to extend corporate/on-premise networks to the cloud as it was part of your network (VPN).

**Important VPC Facts:**
- A VPC is housed within a chosen AWS Region.
- A VPC spans multiple availability zones within a region. This allows to provision redundatn resources on the same network (HA/FT).
- AWS provides a DNS service for your VPC so each instance has a hostname. However, you can run your own DNS servers by changing the DHCP option set configuration within the VPC.

---

Default VPC has an IGW (internet gateway) attached to it and all its subnets are a route to the internet thru it.
Each instance launched in the default VPC has a private and public IP address.

---

**VPC Limits**
- 5 VPCs maximum per region. (can request more)
- 5 internet gateways per region. (only 1 IGW can be attached to each VPC)
- 50 customer gateways per region.
- 50 VPN connections per region.
- 200 route tables per region / 50 entries per route table
- 5 elastic IP addresses
- 500 security groups per VPC
- 50 rules per security group
- 5 security groups per network interface

---

<h2>Basic Components</h2>

**Internet Gateway**
To ensure access to/from open internet to your instances on your VPC you should attach an IGW, ensure that the the (public) Subnet Route Table points to the IGW, instances on your subnet should have a Public or Elastic IP address and ensure that NACL and Security Group rules allow relevant traffic.
- VPC component that allows communication between instances on your VPC and the Internet.
- Is horizontally scaled, redundant and highly available.
- It doesn't impose any availability risk or bandwidth constrain on your network traffic.
- Provides NAT Translation for instances that have public IP addresses (Public/Private IP)


**Route Table**

A Route Table (RT) contains a set of rules, called routes, that are used to determine where network traffic is directed.

A RT is composed of:
- Destination: The CIDR block range of the target (where the data is routed to)
- Target: A name identifier of where the data is being routed to.

By default all subnets traffic is allowed between each other available subnet within your VPC (That's called local route). You cannot modify the local route.
You also cannot delete a route table if it has dependencies (associated subnets).

**Subnet**

When you create a VPC, it spans all of the availability zones in the region. After creating a VPC, you can add one or more subnets in each Availability Zone. Each subnet must reside entirely within one Availability Zone and cannot span zones.

- Subnets MUST be associated with a route table.

- A **Public Subnet** HAS a route to the internet. (It is associated with a route table that has IGW attached)
- A **Private Subnet** DOESN'T have a route to the internet (It is associated with a route table that DOES NOT has IGW attached)

Instances launched in a private subnet cannot communicate with the internet. This creates a higher level of security but also a limitation of instances not being able to download software and/or updates. This last issue can be resolved by using a NAT gateway.
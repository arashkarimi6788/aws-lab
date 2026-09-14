# aws-lab

Exploratory AWS work for Month 4 of the DevOps/network-automation curriculum — VPC, EC2, S3, and container/Kubernetes basics.

## VPC setup (via AWS CLI)

Built a full networking stack from scratch using the AWS CLI, mapping each
piece to familiar networking concepts:

| AWS concept | Analogy | What it does |
|---|---|---|
| VPC (10.0.0.0/16) | Network / address space | Top-level container for everything |
| Subnet (10.0.1.0/24) | VLAN / segment | A slice of the VPC's address space |
| Internet Gateway | Default route to ISP | Gives the VPC a path to the internet |
| Route table (0.0.0.0/0 → IGW) | Static default route | Without this, the IGW alone does nothing |
| Security Group | FortiGate policy | Stateful, allow-list firewall per instance |

Key lesson: attaching an Internet Gateway is not enough on its own — the
subnet needs a route table pointing `0.0.0.0/0` at it, AND
`MapPublicIpOnLaunch` needs to be enabled on the subnet, or instances won't
get a public IP even with working routing.

Verified end-to-end by launching a `t3.micro` EC2 instance (Ubuntu 24.04)
into the subnet and SSHing in successfully from a security-group rule
scoped to a single `/32` source IP.

## Contents
(to be filled in as sections are completed)

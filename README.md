# 🌐 AWS VPC Networking Project

> My first AWS project — building a Virtual Private Cloud (VPC) from scratch and understanding core networking concepts in the cloud.

---

## 📌 Project Overview

This project walks through setting up a fully functional AWS VPC with public and private subnets, route tables, an internet gateway, and security groups. It demonstrates foundational cloud networking skills using the AWS Management Console and AWS CLI.

---

## 🏗️ What I Built

| Component | Details |
|---|---|
| **VPC** | `10.0.0.0/16` — 65,536 available IP addresses |
| **Public Subnet** | `10.0.1.0/24` — for internet-facing resources |
| **Private Subnet** | `10.0.2.0/24` — for internal/backend resources |
| **Internet Gateway** | Attached to VPC to enable public internet access |
| **Route Tables** | Public route table directing `0.0.0.0/0` to the IGW |
| **Security Groups** | Inbound/outbound rules to control traffic |

---

## 🧠 Key Concepts Learned

- **CIDR Blocks** — How IP address ranges work (e.g. `/16` gives 65,536 IPs; `/24` gives 256)
- **Public vs Private Subnets** — Public subnets route to the internet; private subnets stay internal
- **Internet Gateway (IGW)** — The bridge between your VPC and the public internet
- **Route Tables** — Rules that determine where network traffic is directed
- **Security Groups** — Virtual firewalls controlling inbound and outbound traffic at the instance level

---

## 🛠️ AWS Services Used

- Amazon VPC
- AWS CLI
- EC2 (Security Groups)

---

## 🚀 Steps I Followed

1. Created a VPC with CIDR block `10.0.0.0/16`
2. Created a **public subnet** (`10.0.1.0/24`) and a **private subnet** (`10.0.2.0/24`)
3. Created and attached an **Internet Gateway** to the VPC
4. Configured a **route table** for the public subnet to route traffic via the IGW
5. Set up **security groups** with appropriate inbound/outbound rules
6. Verified connectivity and subnet configurations via the AWS Console and CLI

---

## 💻 Useful CLI Commands

```bash
# View all subnets in your VPC
aws ec2 describe-subnets \
  --filters "Name=vpc-id,Values=<your-vpc-id>" \
  --query "Subnets[*].{ID:SubnetId, CIDR:CidrBlock, AZ:AvailabilityZone}" \
  --output table

# Create a subnet
aws ec2 create-subnet \
  --vpc-id <your-vpc-id> \
  --cidr-block 10.0.1.0/24

# Attach an internet gateway to a VPC
aws ec2 attach-internet-gateway \
  --internet-gateway-id <igw-id> \
  --vpc-id <your-vpc-id>
```

---

## 📸 Architecture Diagram

```
                        Internet
                           │
                    Internet Gateway
                           │
              ┌────────────▼────────────┐
              │      VPC 10.0.0.0/16    │
              │                         │
              │  ┌──────────────────┐   │
              │  │  Public Subnet   │   │
              │  │  10.0.1.0/24     │   │
              │  └──────────────────┘   │
              │                         │
              │  ┌──────────────────┐   │
              │  │  Private Subnet  │   │
              │  │  10.0.2.0/24     │   │
              │  └──────────────────┘   │
              └─────────────────────────┘
```

---

## 🙋‍♀️ About Me

**Lenah Mbatha** — Data Analyst & IT Professional based in Nairobi, Kenya.  
Passionate about cloud infrastructure, data monitoring, and digital transformation.

📧 lenahmbatha5@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/lenah-mbatha-4123b2246/)

---

## 📚 Resources

- [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
- [NextWork Project Guide](https://learn.nextwork.org)
- [AWS CLI Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/ec2/index.html)

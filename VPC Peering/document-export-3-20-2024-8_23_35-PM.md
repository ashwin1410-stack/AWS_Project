# ICMP Ping Test for Instances in VPC with VPC Peering

## Objective:
To verify connectivity between instances in different VPCs via VPC peering using ICMP ping.

**Test Setup:** 

- VPC Test [Tag:-Test-VPC,CIDR:-10.0.0.0/16,Subnet CIDR:-10.0.0.0/24,Test-IGW,Test-RT]
- VPC Production[Tag:-Production-VPC,CIDR:-192.0.0.0/16,Subnet CIDR:-192.0.0.0/24,Production-IGW,Production-RT]
**VPC Peering:**

- VPC Peering Connection: VPC Peering connection between Test VPC & Production VPC.
**Instance Configuration:**

- Instance Test: [AMI:-Ubuntu Server,Instance Type:-t2.micro,VPC:-Test VPC,IP:- 10.0.0.147]
- Instance Production:[AMI:-Ubuntu Server,Instance Type:-t2.micro,VPC:-Production VPC,IP:-192.0.0.41]
## Test Procedure:
- **Identify instance: **
Determine the IP addresses  of Instance TEST (in VPC A) and Instance Production (in VPC B).

- **SSH into Instances:** 
SSH into Instance Test & Instance Production to access their command-line interfaces.

- **Ping Test:**
From Instance Test, execute the ICMP ping command to ping Instance Production.

![Screenshot 2024-03-19 140103.png](https://eraser.imgix.net/workspaces/zsmdjrvbVSNikp78ON3c/wDvujyqwbvYnfYNLiDs25jwkruJ3/tUOTQiM93Ti0mz7qcsGkR.png?ixlib=js-3.7.0 "Screenshot 2024-03-19 140103.png")

From Instance Production, execute the ICMP ping command to ping Instance Test.

![Screenshot 2024-03-19 140025.png](https://eraser.imgix.net/workspaces/zsmdjrvbVSNikp78ON3c/wDvujyqwbvYnfYNLiDs25jwkruJ3/p4DKlSBbzNF22IPgZ2chK.png?ixlib=js-3.7.0 "Screenshot 2024-03-19 140025.png")

## **Conclusion:**
Connectivity between instances in VPC-TEST and VPC-PRODUCTION via VPC peering using ICMP ping has been successfully verified.

The test confirms that the VPC peering connection is functioning as expected, allowing communication between instances across different VPCs within the same AWS region. 

## **Observation:**
ICMP ping from Instance Production to Instance Test is successful. Round-trip time and TTL values are within expected ranges.


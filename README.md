# ACL and OSPF Configuration – Step-by-Step Guide

## 📝Task
- Use **OSPF (single area)** for routing between the routers.
- Activate **Telnet/SSH access** on routers for remote management.
- Configure **Access Control Lists (ACLs)** based on the following conditions:

### Access Control Requirements:
- **PC0**:
  - Denied access and denied ping to **Khazar Server**.
- **PC1**:
  - Allowed to access **Khazar Server**, but denied from pinging it.
  - Allowed **SSH access** to **Router1 (2.2.2.2)**.
- **PC2**:
  - Allowed to ping **Khazar Server**, but denied full access.
  - Allowed **SSH access** to **Router1 (2.2.2.2)**.

---

## Configuration Steps

### 1. IP Addressing
- Assign IP addresses to all devices based on the topology.
- Set default gateways on PCs and servers appropriately.

### 2. Enable OSPF on Routers
- Assign a router ID to each router.
- Configure OSPF Area 0.
- Advertise all directly connected networks using `network` commands.

### 3. ACL Configuration
- Create and apply extended access control lists on **Router1 (2.2.2.2)** to control traffic:

#### Example ACL logic (summarized, not actual commands):
- **Deny** PC0 (172.168.1.10) from accessing or pinging **Khazar Server (192.168.1.3)**.
- **Permit** PC1 (172.168.1.11) to access but not ping **Khazar Server**.
- **Permit** PC2 (172.168.1.12) to ping **Khazar Server**, but deny other access.
- Allow **SSH (port 22)** from **PC1** and **PC2** to **2.2.2.2**.
- **Deny all other traffic** as the final rule.

### 4. SSH Configuration on Router1 (2.2.2.2)
- Set a hostname and domain name.
- Create username and password.
- Generate RSA keys.
- Enable SSH and configure VTY lines to accept SSH input only.

### 5. Test and Verify
- From PC0: Confirm it cannot access or ping Khazar.
- From PC1: Confirm it can access Khazar but not ping it, and can SSH to Router1.
- From PC2: Confirm it can ping Khazar but not access it, and can SSH to Router1.
- Use `ping`, `telnet`, `ssh`, and `tracert` commands to verify behavior.

---

## Notes
- Ensure ACLs are applied in the **correct direction** on the correct **interfaces** (inbound/outbound).
- For SSH to work, confirm each PC has an IP route and DNS setup (if needed) to reach 2.2.2.2.
## Project Files

- `.pkt` file containing the full Packet Tracer simulation.
--
## Additional Information

- All routers have **hw7** enable password.

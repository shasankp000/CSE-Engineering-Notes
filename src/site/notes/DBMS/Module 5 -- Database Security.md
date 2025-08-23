---
{"dg-publish":true,"permalink":"/dbms/module-5-database-security/","title":"Module 5 -- Database Security -- DBMS","tags":["Semester-6","DBMS"],"created":"2025-05-20T00:58:46.934+05:30"}
---

---
# Index

1. [[#Authentication]]
2. [[#2. Authorization and Access Control]]
3. [[#1. Discretionary Access Control (DAC)]]
4. [[#2. Mandatory Access Control (MAC)]]
5. [[#3. Role based Access Control]]
6. [[#3. Intrusion Detection]]
7. [[#Working of Intrusion Detection System(IDS)]]
8. [[#4. SQL Injection]]

---
# Authentication

### 1. **Authentication**

- Verifies **who** is accessing the database.
    
- Common methods:
    
    - Username/password
    - Biometric login
    - Tokens or 2FA (two-factor authentication)

> 🔑 Think of it as a **gatekeeper** asking: _"Are you really who you claim to be?"_


---
# 2. Authorization and Access Control

- Defines **what** a user is allowed to do:
    - Read, write, delete, update tables
    - Access certain rows or columns
- Based on privileges/roles assigned by the DB admin.

> 🛡️ Think: _"Okay, you’re in. But what can you do here?"_

---
# Access Control Models

## 1. Discretionary Access Control (DAC)


![Pasted image 20250520224206.png](/img/user/media/Pasted%20image%2020250520224206.png)

### 🔸 Definition:

In **DAC**, the **data owner (user)** decides who gets access and what kind of access (read/write/execute) they get.

- It’s called “**discretionary**” because the control is left to the discretion of the owner.

### 🔸 Example:

If you create a table, you can grant read or write access to any user you choose.

```sql
GRANT SELECT ON Employee TO User1;
```
### 🔸 Pros:

- Easy to manage in small systems.
- Very flexible — users have full control over their own data.
### 🔸 Cons:

- **Security risks**: Users may grant access to unauthorized users.
- Hard to manage in large organizations.
### 🔸 Use Case:

- Personal file sharing systems, small teams.

---
## 2. Mandatory Access Control (MAC)

![Pasted image 20250520224457.png](/img/user/media/Pasted%20image%2020250520224457.png)

### 🔸 Definition:

**MAC** is a **strict, non-discretionary** model where access is governed by a **central authority** using **security labels**.

- Every user and piece of data is given a **security level** (e.g., Confidential, Secret, Top Secret).
- A user can only access data if their level **dominates or matches** the data’s level.

### 🔸 Example:

- A user with a “Secret” clearance can access “Secret” and “Confidential” data, but not “Top Secret”.
### 🔸 Pros:

- **Highly secure**.
- Prevents accidental or intentional data leaks.
### 🔸 Cons:

- Very rigid — no user control.
- Complex to set up and maintain.
### 🔸 Use Case:

- Military, intelligence, or classified government systems.

---
## 3. Role based Access Control

![Pasted image 20250520224547.png](/img/user/media/Pasted%20image%2020250520224547.png)

### 🔸 Definition:

In **RBAC**, permissions are assigned to **roles**, not individuals. Users are assigned to roles, and get the permissions of that role.

- Roles reflect real-world job functions (e.g., “Student”, “Teacher”, “Manager”).

### 🔸 Example:

- The “Manager” role can read/write reports, while the “Employee” role can only read them.

```sql
-- Assign permissions to role
GRANT SELECT, INSERT ON Reports TO Manager;

-- Assign user to role
GRANT Manager TO Alice;
```
### 🔸 Pros:

- **Scalable** and organized.
- Easier to manage in large systems.
### 🔸 Cons:

- Less flexible than DAC for ad-hoc sharing.
- Requires careful planning of roles.
### 🔸 Use Case:

- Enterprise systems, universities, banking software.

---
## 🔁 **Comparison Table**

|Feature|DAC|MAC|RBAC|
|---|---|---|---|
|Who controls access|Owner/user|Central authority|Role-based (admin defined)|
|Flexibility|High|Low|Medium to High|
|Security Level|Medium|High|High|
|Suitable For|Small systems|Military, Government|Large enterprises, organizations|
|Can users share access?|Yes|No|Not directly, only through roles|
|Examples|Unix file permissions|Classified document systems|ERP systems, CMS platforms|

---
# 3. Intrusion Detection

https://www.geeksforgeeks.org/intrusion-detection-system-ids/

- Monitors for **suspicious or unauthorized activities** in the database.
- Alerts or blocks potential attackers.
- Two types:
    
    - **Anomaly-based**: Flags anything unusual.
    - **Signature-based**: Looks for known attack patterns.

## Common Methods of Intrusion

- **Address Spoofing:** Hiding the source of an attack by using fake or unsecured proxy servers making it hard to identify the attacker.
- **Fragmentation**: Sending data in small pieces to slip past detection systems.
- **Pattern Evasion:** Changing attack methods to avoid detection by IDS systems that look for specific patterns.
- **Coordinated Attack:** Using multiple attackers or ports to scan a network, confusing the IDS and making it hard to see what is happening.

## Working of Intrusion Detection System(IDS)

- An IDS (Intrusion Detection System) monitors the traffic on a computer network to detect any suspicious activity.
- It analyzes the data flowing through the network to look for patterns and signs of abnormal behavior.
- The IDS compares the network activity to a set of predefined rules and patterns to identify any activity that might indicate an attack or intrusion.
- If the IDS detects something that matches one of these rules or patterns, it sends an alert to the system administrator.
- The system administrator can then investigate the alert and take action to prevent any damage or further intrusion.

![Pasted image 20250520224859.png](/img/user/media/Pasted%20image%2020250520224859.png)

## **Classification of Intrusion Detection System(IDS)**

(I just copied this from geeksforgeeks, no need go too much in-depth, just get a basic idea of this).

 Intrusion Detection System are classified into 5 types:

- **Network Intrusion Detection System (NIDS):** ==Network intrusion detection systems (NIDS) are set up at a planned point within the network to examine traffic from all devices on the network. It performs an observation of passing traffic on the entire subnet and matches the traffic that is passed on the subnets to the collection of known attacks==. Once an attack is identified or abnormal behavior is observed, the alert can be sent to the administrator. An example of a NIDS is installing it on the subnet where [firewalls](https://www.geeksforgeeks.org/introduction-of-firewall-in-computer-network/) are located in order to see if someone is trying to crack the [firewall](https://www.geeksforgeeks.org/introduction-of-firewall-in-computer-network/).

- **Host Intrusion Detection System (HIDS):** ==Host intrusion detection systems (HIDS) run on independent hosts or devices on the network. A HIDS monitors the incoming and outgoing packets from the device only and will alert the administrator if suspicious or malicious activity is detected. It takes a snapshot of existing system files and compares it with the previous snapshot. If the analytical system files were edited or deleted, an alert is sent to the administrator to investigate==. An example of HIDS usage can be seen on mission-critical machines, which are not expected to change their layout.

- **Hybrid Intrusion Detection System:** ==Hybrid intrusion detection system is made by the combination of two or more approaches to the intrusion detection system. In the hybrid intrusion detection system, the host agent or system data is combined with network information to develop a complete view of the network system==. The hybrid intrusion detection system is more effective in comparison to the other intrusion detection system. Prelude is an example of Hybrid IDS.

- **Application Protocol-Based Intrusion Detection System (APIDS):** An application [Protocol-based Intrusion Detection System](https://www.geeksforgeeks.org/intrusion-detection-system-ids/) (APIDS) is a ==system or agent that generally resides within a group of servers. It identifies the intrusions by monitoring and interpreting the communication on application-specific protocols==. For example, this would monitor the SQL protocol explicitly to the middleware as it transacts with the database in the web server.

- **Protocol-Based Intrusion Detection System (PIDS):** ==It comprises a system or agent that would consistently reside at the front end of a server, controlling and interpreting the protocol between a user/device and the server==. It is trying to secure the web server by regularly monitoring the [HTTPS protocol](https://www.geeksforgeeks.org/explain-working-of-https/) stream and accepting the related [HTTP protocol](https://www.geeksforgeeks.org/http-full-form/). As HTTPS is unencrypted and before instantly entering its web presentation layer then this system would need to reside in this interface, between to use the HTTPS.

- **Signature-Based Detection:** ==Signature-based detection checks network packets for known patterns linked to specific threats. A signature-based IDS compares packets to a database of attack signatures and raises an alert if a match is found==. Regular updates are needed to detect new threats, but unknown attacks without signatures can bypass this system.
---
## Benefits of IDS

- ***Detects Malicious Activity:*** IDS can detect any suspicious activities and alert the system administrator before any significant damage is done.
- ***Improves Network Performance:*** IDS can identify any performance issues on the network, which can be addressed to improve network performance.
- ***Compliance Requirements:*** IDS can help in meeting compliance requirements by monitoring network activity and generating reports.
- ***Provides Insights:*** IDS generates valuable insights into network traffic, which can be used to identify any weaknesses and improve network security.

---
## Disadvantages of IDS

- ***False Alarms***: IDS can generate false positives, alerting on harmless activities and causing unnecessary concern.
- ***Resource Intensive***: It can use a lot of system resources, potentially slowing down network performance.
- ***Requires Maintenance***: Regular updates and tuning are needed to keep the IDS effective, which can be time-consuming.
- ***Doesn't Prevent Attacks***: IDS detects and alerts but doesn’t stop attacks, so additional measures are still needed.
- ***Complex to Manage***: Setting up and managing an IDS can be complex and may require specialized knowledge.

---
# 4. SQL Injection 

- A type of attack where **malicious SQL code is inserted** into input fields.
- Can expose or destroy data.

For example,

```sql
SELECT * FROM users WHERE username = 'admin' --' AND password = '';
```
The `--` comments out the rest, bypassing the password check.

This can be prevented by:

- Using **prepared statements** or **parameterized queries**
- Validating user inputs
- Escaping special characters

---
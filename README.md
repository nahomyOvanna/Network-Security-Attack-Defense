# **Network Security: Attack & Defense**

## Objective

Simulate a network attack and defense by performing an Nmap scan, configuring a firewall on Ubuntu, and capturing traffic with Wireshark to analyze the impact of security measures.

## Skills Learned

- Network scanning with Nmap
- Configuring firewalls (UFW)
- Traffic capture and analysis with Wireshark
- Documenting findings and creating network diagrams

## Tools Used

- Ubuntu (Target VM)
- Kali Linux (Attacker VM)
- Nmap
- UFW (Firewall)
- Wireshark

## Steps



### 1. **Find the IP Address of Ubuntu** 🖥️🔍
   
- On the Ubuntu VM, open the terminal and run:  **ip a**

![1](https://github.com/user-attachments/assets/934f7a78-bd75-4bf6-a454-f53476dc427a)

- Note the IP address (e.g., 10.0.2.15) from the inet field.



### 2. **Find the IP Address of Kali Linux** 🖥️🔍

- On the Kali Linux VM, open the terminal and run:   **ip a**

![2](https://github.com/user-attachments/assets/67f26443-41f6-4d7a-943a-74f33293b0a8)

- Note the IP address (e.g., 10.0.2.6) from the inet field.



### 3.  **Launch an Nmap Scan from Kali Linux** 🚨🛠️

- On Kali Linux, open the terminal and run:   **nmap -A 10.0.2.15**

![3](https://github.com/user-attachments/assets/2ced2a78-8efb-4103-8eda-ae2916e39ccb)

- This will scan the Ubuntu machine and generate a report.



### 4. **Set Up a Firewall on Ubuntu** 🔥🛡️

- To block unauthorized access, set up a firewall on Ubuntu:

 a. **sudo apt install ufw**

![4 1](https://github.com/user-attachments/assets/2f3c5413-5f40-46d0-b251-91561d708ba5)

  b. **sudo ufw enable**

 ![4 2](https://github.com/user-attachments/assets/0accacd6-6d66-401a-81ce-d3cb9cc67d37)

  c. **sudo ufw allow ssh**

 ![4 3](https://github.com/user-attachments/assets/64fd57b3-1606-4f01-b3c2-24c1af109309)

  d. **sudo ufw allow from 10.0.2.6**

  ![4 4](https://github.com/user-attachments/assets/ac2722f2-fecb-40dc-a769-d90cb9f11462)

  e. **sudo ufw status**

   ![4 5](https://github.com/user-attachments/assets/1cbc3f74-eee8-434a-a00f-da3beb719045)

- This will activate the firewall and allow connections only from Kali Linux.



### 5. **Install Wireshark on Ubuntu** 💻🔧

- To capture network traffic, install Wireshark on Ubuntu:

  **sudo apt install wireshark**

![5](https://github.com/user-attachments/assets/9b66aea3-e0ba-43d1-b4c9-488d6c3a1f31)

- Follow the prompts to complete installation.  



### 6. **Capture Network Traffic with Wireshark** 🐟🔎

- Open Wireshark on Ubuntu by running:  **sudo wireshark**

![6](https://github.com/user-attachments/assets/4ccb49e4-9e64-4d83-9ae4-0ced3ebc6b1b)

- Start capturing network traffic.

![6 1](https://github.com/user-attachments/assets/fb9b6086-ebdd-4cc1-9c1b-a3ddce741f5f)

![6 2](https://github.com/user-attachments/assets/eb3aaa0d-4aea-4318-a6ab-e329859dd687)



### 7. **Re-run the Nmap Scan from Kali Linux** 🔄🧑‍💻🔍

- On Kali Linux, run the Nmap scan again: **nmap -A 10.0.2.15**

![7](https://github.com/user-attachments/assets/e8dcac53-685a-4677-9e2f-8373d2880ca4)

![7 1](https://github.com/user-attachments/assets/5944b756-d6ba-4b99-94e9-c70f093ba9ef)

![7 2](https://github.com/user-attachments/assets/c1ae558c-fb63-4f05-8e71-1e4aef9911db)

- Capture the traffic in Wireshark on Ubuntu.



### 8. **Network Diagram** 🗺️🔗

                            +------------------+
                            |    VirtualBox    |
                            +------------------+
                                    |
                                    |
                      +-------------+--------------+
                      |                            |
         +---------------------+        +-------------------+
         |     Ubuntu VM        |        |   Kali VM         |
         |    (IP: 10.0.2.15)   |        |  (IP: 10.0.2.6)   |
         +---------------------+        +-------------------+
                |                            |
                |                            |
      +---------------------+    +----------------------+
      |     NAT Network      |    |     NAT Network      |
      +---------------------+    +----------------------+
                |                            |
                +----->  Firewall (UFW) <----+
                      (Ubuntu)
                |
        +---------------------+
        |   Wireshark Capture |
        |   (Ubuntu VM)        |
        +---------------------+

**The network setup was visualized using a diagram, which includes:**

   1.	VirtualBox host machine.
   2.	Two VMs: Ubuntu and Kali Linux connected through a NAT Network.
   3.	Nmap scan from Kali to Ubuntu.
   4.	UFW firewall on Ubuntu blocking all traffic except from Kali.
   5.	Wireshark capturing network traffic during the attack.



 ## Conclusion: ✅🔒📊

This project demonstrated how to simulate a network attack and defense. Using Nmap, I identified vulnerabilities on Ubuntu, then configured a firewall (UFW) to block unauthorized access. Wireshark captured network traffic, showing the effectiveness of the firewall in blocking attack attempts. The project provided hands-on experience with network scanning, firewall configuration, and traffic analysis, reinforcing key concepts in network security.


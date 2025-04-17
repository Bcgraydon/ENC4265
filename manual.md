[Home](index.md) | [Manual Assessment Memo](manual_assessment_memo.md) | [Chatbot](chatbot.md) | [Procedure Video](procedure_video.md) | [Manual](manual.md) | [Reflective Blogs](reflective_blogs.md)
# Building a Home Cybersecurity Lab for Learning and Testing
 
*By Benjamin Graydon*  
*ENC 4265 - Spring 2025*  
*April 2025*  

---

## Table of Contents
- [Introduction](#introduction)
- [What is a Home Network Lab?](#what-is-a-home-network-lab)
- [Why Build One?](#why-build-one)
- [Required Equipment](#required-equipment)
- [Networking Concepts Overview](#networking-concepts-overview)
- [Network Diagram Setup](#network-diagram-setup)
- [Hardware Setup Instructions](#hardware-setup-instructions)
  - [Setting up the Router](#setting-up-the-router)
  - [Switch Configuration](#switch-configuration)
  - [Connecting Devices](#connecting-devices)
- [Installing Virtual Machines](#installing-virtual-machines)
  - [Using VirtualBox](#using-virtualbox)
  - [Installing Kali Linux](#installing-kali-linux)
  - [Installing Metasploitable](#installing-metasploitable)
- [Optional Physical Lab Setup](#optional-physical-lab-setup)
- [Using the Lab](#using-the-lab)
  - [Running Scans with Nmap](#running-scans-with-nmap)
  - [Capturing Packets with Wireshark](#capturing-packets-with-wireshark)
  - [Pen Testing in a Safe Environment](#pen-testing-in-a-safe-environment)
- [Troubleshooting](#troubleshooting)
- [FAQs](#faqs)
- [AI Statement](#ai-statement)
- [Works Cited](#works-cited)

---

## Introduction
Building your own home cybersecurity lab is one of the best ways to gain hands-on experience in networking, system administration, penetration testing, and ethical hacking. This manual will walk you through everything from basic setup to advanced usage.

Unlike commercial networks, your home lab is a safe, sandboxed environment where you can freely test tools like Nmap, Wireshark, and Kali Linux without risking any real systems. Whether you're pursuing a cybersecurity career or just want to understand how the internet works, this guide will help you get started.

This manual uses Markdown to document each step and provide hyperlinks, images, and explanations for both the "how" and the "why" behind every task.


> <img src="https://johnkeen.tech/wp-content/uploads/2021/11/IMG_9841-Large.jpeg" alt="Home Network Diagram" width="400" />

<p style="text-align: center;"><em>Figure 1: Home Network Diagram, source: John Keen Tech</em></p>


---

## What is a Home Network Lab?
A home network lab is a self-contained environment where you can simulate real-world IT systems and test cybersecurity tools and concepts. It usually consists of virtual machines (VMs), networked devices, routers, and switches configured in a way that mimics enterprise infrastructure.

You can build a lab entirely with software on a single computer using virtualization tools, or expand into physical equipment like Raspberry Pis, routers, and switches. The goal is to create a safe space where you can break things, fix them, and learn by doing.

---

## Why Build One?
There are many benefits to setting up a home network lab:

- **Hands-on Learning**: Reading about networking and cybersecurity is useful, but doing it makes the knowledge stick.
- **Certifications Prep**: Labs are ideal for practicing skills needed for CompTIA Network+, Security+, CEH, and other certifications.
- **Job Skills**: Building and troubleshooting networks mirrors tasks you’ll do in real IT or cybersecurity roles.
- **Safe Testing**: You can safely explore penetration testing, malware analysis, and traffic sniffing without risking legal or ethical issues.
- **Flexibility**: Your lab can evolve as your skills grow — from basic router config to building a simulated corporate network.

Whether you're just starting or building toward a career, a home network lab gives you a playground to explore, learn, and sharpen your skills.

---

## Required Equipment
You don’t need expensive gear to start a home network lab. Many setups can be done entirely on your current PC using virtualization software. Here's a breakdown of what's recommended:

###  Basic Essentials:
- **Computer with at least 16GB RAM** – Needed to run multiple virtual machines smoothly

  [16 Gb Ram Kit from Amazon](https://www.amazon.com/NVTEK-DDR3-1600-PC3-12800-Non-ECC-Desktop/dp/B0939P6L74/ref=sr_1_1_sspa?crid=1QK57TJXRL9VI&dib=eyJ2IjoiMSJ9.Y5399RiXuQi6-L48o49OO7K7Yf9p4pyeOBkeaqtXlV4nlXNmDR0quZn1galwE5Ra31i-9ccpuKOT2Gj3O3RfNyPE16qF_aZdYN0jJW7b703VkaMbRb9KxwBVNl2cTmbcwnFOCtUfmtGYpRghHi3LQ7rh5MuB6X_uVyX6MmpR-FFi9an-7gsJwJZN32k1xNVX5bZ9wBfrI9LUwqDyFx1ezDwkyjGYNuHq6lPXvRCl1bM.MA8mkTn2odhRsKhrN_NMBB0oQoBho-Z32wA7b0vvrKU&dib_tag=se&keywords=16%2Bgb%2Bram&qid=1744830820&sprefix=16%2Bgb%2Bram%2B%2Caps%2C147&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)
- **Virtualization software** – VirtualBox (free), VMware Workstation Player (free for personal use)

  [VirtualBox download](https://www.virtualbox.org/wiki/Downloads)
- **Operating system ISOs** – e.g., Kali Linux, Ubuntu Server, Metasploitable

  [Kali Linux download](https://www.kali.org/get-kali/#kali-virtual-machines)
- **Reliable Internet connection** – To download tools and updates

###  Optional Hardware:
- **Router** – A spare router can be used to isolate lab traffic

 [Cheap Router from Amazon](https://www.amazon.com/Setup-Wireless-Wi-Fi-Router-Internet/dp/B0CGLWPS5T/ref=sr_1_5_sspa?crid=2RX72K0QR6JNQ&dib=eyJ2IjoiMSJ9.9Gj47GvQNSWzSMKR6iOj0K_2_2RYryvTTOC5_iVIgZkjyVdNCfbsRv1yAY2q_m40QZ4wrXRvB1KXJqG0dYAejgoq1gElym8xNiWrGFpSXwC1Bv_WiVZHpBwCX9SbM-kTB05s1GHXOz5t8pdmWQHSI5WCKc8UamL1Kck9ssk0wZx4IVhNYK_hTf4Ii0IfPOHxLVIgH8o6kJfiTCh9SH6xBEpiZoEjArsRioUgALHRWjAdLXsfI5tqCFESJf7wy_yi-gGFeLVguUrx4Hm44sWxCxYZePjHZQFbSWd-jWUF4cA.20aJZO1O8gtcI9eb7Q0wawN7Wt233kIQ9gw3I41ZdDc&dib_tag=se&keywords=router&qid=1744831132&sprefix=router%2Caps%2C177&sr=8-5-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)
- **Network Switch** – Useful for connecting multiple physical devices

  [Cheap Network Switch from Amazon](https://www.amazon.com/Ethernet-Splitter-Optimization-Unmanaged-TL-SG105/dp/B00A128S24/ref=sr_1_1_sspa?crid=1N2SS7UQ7LNI4&dib=eyJ2IjoiMSJ9.zm2b2eGNCSReGFJuUskv6-s3cUVDK12lfqOmf729JjyTNQU9BmcYqPH1zR4W3AI6ChBAyGCpu30nmqgic4jJuBGtHXoCZQLvHTgZ_5qT-uBUG_33GNm_3yFGeYde_4HlhyUXH8aZgcpUuhnPuWYG1AEVzOHe3AAudKFuLIMAX7ctOgDeRQLhYION8KlcyEVWC74o2Wd20fuBfCqcqpoIjkFoXWaG3mfgo1UivOD-HlE.rb__vW4ED-Kroc7rGJLbRJ5LLrQDSjZbkWeXLKHWWWU&dib_tag=se&keywords=network%2Bswitch&qid=1744831306&sprefix=network%2Caps%2C187&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)
- **Raspberry Pi or spare laptops** – Acts as servers, DNS, firewall, or targets for testing
- **Old PCs or thin clients** – Can be repurposed as part of your lab

###  Optional Accessories:
- **USB Wi-Fi adapters** – Useful for wireless testing

  [Wifi Adapter from Amazon](https://www.amazon.com/Wireless-USB-WiFi-Adapter-PC/dp/B07J65G9DD/ref=sr_1_2_sspa?crid=21EBSIXE6MFAD&dib=eyJ2IjoiMSJ9.Cpk9qEaP8FCv_AaXO1XwmXpIoTCueAWMOH9NU-eckUNzNQSjESW-nxtYQ2k9bV6KxLY2pS-Qlx1IaueKfqJeDo6HNljx4IMpkxJCEFGu1NH0cJoaObhq1wA4zkDMRxwPQdGKq5YSUK3bkUAQgSkuljdj23pxcclKVk5y1qdSIa_uyRMnFgYE1jZCKsofplxwBX89PK8ggUnbZpPJP60zN3pDEtuX5__BjhJs7-CFing.izt67dJQ4Nr-O9gOlKW9F5kylerKp675n4YNt74o0Ao&dib_tag=se&keywords=USB+Wi-Fi+adapters&qid=1744831489&sprefix=usb+wi-fi+adapters%2Caps%2C150&sr=8-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1)
- **Ethernet cables** – If building a physical network

  [10ft Cable from Amazon](https://www.amazon.com/Amazon-Basics-Ethernet-High-Speed-Snagless/dp/B089MGNQXF/ref=sr_1_7_ffob_sspa?crid=2O6K89ND7NRRU&dib=eyJ2IjoiMSJ9.Qrm0YFmTEww5DZc4mrTYoNn-bpwOCt5sbXP4W_xXulJeleuZV9enl7iyOHP0WcLRfWhJuEzjU7oi2FCDedZABFqAHa339Gg-g4DOhL1qEnXixPxTk5bnl4-IU1dF6zuERHHddE4z1LHZGYQkjNH9XbuIuJFJeuQYNstgR9UXimdgFpna17cBNFCcd5GKl8qS4fCQCinIPKZriU93rzqGfRMjUOQox1wA2KX222VTbHc.fLKhT7-JGYbPe60uX5mDRtJGLxGHkV9Qyiz2HljiSes&dib_tag=se&keywords=ethernet%2Bcable&qid=1744831696&sprefix=ethernet%2B%2Caps%2C162&sr=8-7-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9tdGY&th=1)
- **KVM switch** – If using multiple machines with one monitor/keyboard/mouse

  [KVM switch from Amazon](https://www.amazon.com/Switcher-Computers-Keyboard-Selector-Compatible/dp/B0CHY8L11W/ref=sr_1_1_sspa?crid=8499PZ40WD7X&dib=eyJ2IjoiMSJ9.gAOq7cNdIDPvIcj3wSUTdTLnAg8joLb2VUA4MDFRWGuwo8XFMo8ZXLMUAZoAzoZG0mJ1C86VlAYTuTD2_NKroWz3pBsMxVd-kva3__RSr-4C7OQXGdGHpSM2CyskfioGs_aqEgydqG4HXBZ36EE2DkDvGr-ONx347L-Cul74Xf8ZZv0WEOll1IA2I9691udKVA_Lq0jfDIt4BX64oCd97yNyHArq_ZHHJMvdNudBn-w.urDZlE7_Nhu8vTtF7P2_A2OucLRivK0OMBp87UsXjsM&dib_tag=se&keywords=kvm+switch&qid=1744831816&sprefix=kvm+%2Caps%2C151&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1)

Start small with virtual machines and scale up to hardware as your interests grow. The next section will help you understand the networking basics you'll apply to your lab.

---

## Networking Concepts Overview
Before jumping into the physical or virtual setup, it's important to understand a few basic networking concepts. These ideas are essential for setting up devices, testing traffic, and understanding what’s really going on in your lab.

###  IP Addresses
Every device on a network needs an IP address. Home networks typically use private IP ranges like `192.168.x.x`. Devices are either:
- **Static** (manually assigned)
- **Dynamic** (assigned by DHCP from your router)

###  Subnets
Subnets break large networks into smaller segments. This helps organize and manage traffic efficiently. You'll most likely use a /24 subnet (e.g., `192.168.1.0/24`) in your lab.

###  Routers vs Switches
- **Routers** connect different networks and assign IP addresses.
- **Switches** allow multiple devices within the same network to communicate.

###  DNS, DHCP, and NAT
- **DNS**: Translates domain names to IPs (like `google.com` → `8.8.8.8`)
- **DHCP**: Automatically assigns IPs
- **NAT**: Lets private devices share a single public IP to access the internet

###  Firewalls
A firewall monitors and controls incoming/outgoing traffic. You’ll explore both hardware firewalls (via router settings) and software firewalls (like UFW in Linux).

Understanding these concepts will help you plan your lab network and troubleshoot problems more effectively in later sections.

---

## Network Diagram Setup
A network diagram is a visual layout that shows how devices in your lab are connected. It helps you understand the data flow, plan your IP address assignments, and identify where each service lives.

You can draw your diagram using tools like:
- [draw.io](https://app.diagrams.net/)
- [Lucidchart](https://www.lucidchart.com/)
- [Google Drawings](https://docs.google.com/drawings)
   
### Example Virtual Lab Diagram: 

### Key Tips:
- Assign each device a static IP address so they don’t change after rebooting.
- Keep “attacker” tools isolated from your home network using a separate router or VirtualBox internal network.
- Label your diagrams clearly with IPs and roles (e.g., attacker, target, user).

A clear diagram makes troubleshooting and expansion easier as your lab grows.

---

## Hardware Setup Instructions
This section walks through how to connect your home lab devices. Whether you're working with virtual machines, physical hardware, or both, getting the physical or virtual wiring right is critical.

### Setting up the Router
1. Plug your lab router into your main router via the WAN/Internet port.
2. Access the router's admin page by entering its IP (e.g., `192.168.1.1`) in a web browser.
3. Change the default login credentials immediately.
4. Set a new subnet range for the lab (e.g., `192.168.2.x`) to keep it separate from your home network.
5. Enable DHCP or set static IPs for connected devices.

### Switch Configuration
1. If using a managed switch, connect to its web interface and assign VLANs or static IPs.
2. For unmanaged switches, simply plug in the Ethernet cables — they handle traffic automatically.
3. Connect devices like Raspberry Pis or old laptops via Ethernet.

### Connecting Devices
1. Connect your primary PC (with VirtualBox) to the lab switch or router.
2. Power on all devices and confirm they have IP addresses in the correct range.
3. Use the `ping` command to test connectivity between devices.
4. Label your devices and cables to keep track of roles.

Once your devices are connected and talking to each other, you're ready to install virtual machines and start testing.

---

## Installing Virtual Machines
Virtual machines (VMs) allow you to simulate multiple computers on one system. This is the backbone of a virtual lab environment. You’ll install VirtualBox, create VMs, and load them with penetration testing and target systems.

### Using VirtualBox
1. Download and install [VirtualBox](https://www.virtualbox.org/) on your host machine.

> <img src="https://github.com/user-attachments/assets/9d534fbf-0046-4027-837e-55ca49b8eb2f" alt="vb" width="400" />

<p style="text-align: center;"><em>Figure 2: VirtualBox download page, captured by Benjamin Graydon</em></p>

3. Launch VirtualBox and click **New** to create a new virtual machine.
4. Name the VM (e.g., `KaliLinux`), select **Linux** as the type, and choose the appropriate version (e.g., **Debian (64-bit)**).
5. Allocate RAM (2GB minimum for Kali, more if you can).
6. Create a virtual hard disk (VDI), at least 20GB in size.
7. Once created, click **Settings > Storage**, and mount your ISO under the optical drive.
8. Start the VM and follow the OS installation steps.

Once installed, take a snapshot of your VM so you can roll back changes after testing.

Next up, you’ll install specific OS images like Kali Linux and Metasploitable for use in your lab.

---

## Installing Kali Linux
Kali Linux is a Debian-based Linux distribution used by cybersecurity professionals for penetration testing, forensics, and reverse engineering. It comes with a large suite of preinstalled tools, making it perfect for ethical hacking in your lab.

### Steps to Install Kali Linux in VirtualBox
1. Download the ISO from the official site: [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)

  > <img src="https://github.com/user-attachments/assets/ebed805d-7b51-402e-83f3-845851044d31" alt="kali" width="400" />

<p style="text-align: center;"><em>Figure 3: Kali Linux download, captured by Benjamin Graydon</em></p>

3. Open VirtualBox and click **New**.
4. Name the VM `KaliLinux`, set the type to **Linux**, and version to **Debian (64-bit)**.
5. Assign at least 2GB of RAM (more if your system allows).
6. Create a virtual hard disk, VDI type, dynamically allocated, at least 20GB.
7. Mount the Kali ISO by going to **Settings > Storage**, clicking on the disk icon next to Optical Drive, and selecting the ISO.
8. Start the VM and follow the Kali installation steps:
   - Choose **Graphical Install**
   - Set hostname (e.g., `kali-lab`)
   - Create a user and set a strong password
   - Use entire disk for partitioning
   - Install the GRUB bootloader when prompted

Once installed, log in and open a terminal to verify tools like `nmap`, `netcat`, and `wireshark` are available.

### Post-Installation Configuration
- Update the system: `sudo apt update && sudo apt upgrade`
- Take a snapshot of the VM so you can revert if something breaks
- Optional: install `guest additions` for better display and input support

Kali is now ready for use in penetration testing exercises within your lab environment.

---

## Installing Metasploitable
Metasploitable is a vulnerable Linux-based virtual machine used to practice penetration testing. It’s intentionally insecure, making it ideal for learning how attackers exploit systems and how defenders can detect and protect against them.

### Steps to Install Metasploitable in VirtualBox
1. Download the Metasploitable VM as a preconfigured VirtualBox appliance (OVA):  
   [https://sourceforge.net/projects/metasploitable/](https://sourceforge.net/projects/metasploitable/)

  > <img src="https://github.com/user-attachments/assets/3502b775-aef8-4702-a680-dbd00cab2d82" alt="Meta" width="400" />

   <p style="text-align: center;"><em>Figure 4: Metasploitable download, captured by Benjamin Graydon</em></p>


3. In VirtualBox, go to **File > Import Appliance**.
4. Select the downloaded `.ova` file and click **Next**.
5. Accept default settings or adjust RAM/CPU settings as needed.
6. Click **Import** to add Metasploitable to your VM list.
7. Start the VM. It will boot to a login screen.

### Default Credentials
- Username: `msfadmin`
- Password: `msfadmin`

You don’t need to install anything manually — the system is ready out of the box. Once logged in, confirm the IP address by running:

``bash
ifconfig

---

## Optional Physical Lab Setup
While virtual labs are flexible and easy to scale, you may want to include physical hardware in your setup to replicate more realistic environments or practice with network cabling and device configuration.

### Common Physical Components
- **Raspberry Pi**: Small, low-power, and highly versatile. Can be used as DNS servers, firewalls, honeypots, or targets.
- **Old laptops or desktops**: Can be installed with Linux or Windows and configured as domain controllers, file servers, or vulnerable machines.
- **Network switches and routers**: Helps practice VLANs, subnetting, and port forwarding.
- **Firewall appliances**: pfSense or OPNsense on a dedicated box for simulating perimeter defense.

### Why Add Physical Devices?
- Adds realism to your practice, including physical troubleshooting.
- Helps learn hardware configuration, cabling, and power management.
- Simulates environments found in small businesses or home offices.

### Setup Considerations
- Use a separate power strip and surge protector for safety.
- Place equipment on a rack or shelf to avoid overheating.
- Label all Ethernet cables and ports for easier debugging.
- Isolate lab hardware from your main network using VLANs or a second router.

Adding physical devices isn't required, but it's a great way to expand your lab if you have the budget and space. It can also make your lab feel more tangible and professional.

---

## Using the Lab
With Kali Linux and Metasploitable running on the same virtual network, you're ready to begin hands-on exercises. This section shows how to run scans, capture traffic, and perform basic penetration testing within your lab.

### Running Scans with Nmap
Nmap is a powerful network scanning tool used to discover devices, open ports, and services.

**Example Commands:**
``bash
nmap -sn 192.168.56.0/24       # Ping scan to list active devices
nmap -sV 192.168.56.102        # Service version scan on target
nmap -p- 192.168.56.102        # Scan all 65535 ports on a host

---

## Troubleshooting
When working with a home cybersecurity lab, you might encounter a few common problems. Here are solutions to typical issues you may face when setting up or using your environment.

### Virtual Machine Won’t Start
**If your VM doesn't boot, crashes on launch, or never leaves a black screen.**
- Make sure virtualization is enabled in your system BIOS.  
- Close any other programs using virtualization (e.g., Docker, VMware).  
- Check RAM allocation; don’t exceed your system’s total memory.

### Devices Can’t Ping Each Other
**If you try to `ping` another device and get "Destination Host Unreachable" or "Request Timed Out."**
- Ensure both VMs are on the same virtual network (Host-Only or Internal).  
- Verify firewall settings on each VM.  
- Double check IP addresses and subnet masks.

### No Internet Connection in the Lab
**If your VM can’t load websites or access online tools.**
- If your VMs need internet, use a NAT adapter in VirtualBox.  
- Alternatively, use a bridged adapter if you understand the risks.

### Kali Linux Is Laggy or Freezes
**If Kali responds slowly, lags when you move the mouse, or freezes entirely.**
- Increase the VM’s RAM and video memory.  
- Install Guest Additions for smoother graphics and input.

### Metasploitable Doesn’t Respond
**If you can’t interact with Metasploitable or `ping` it from another machine.**
- Confirm the VM is running and logged in.  
- Run `ifconfig` to check the IP address.  
- Ping from Kali to verify the connection.

### Wireshark Shows No Traffic
**If your packet capture shows zero results or no new data.**
- Make sure you selected the correct network interface.  
- Try restarting the capture or using a different filter.

>  **Pro Tip:** Use snapshots often and write down any fixes you discover. Troubleshooting is part of the learning process — and it’s good practice for real-world network administration.


---

## FAQs

### Do I need a powerful computer to build a network lab?
A computer with at least 16GB of RAM is recommended to run multiple virtual machines, but you can start with less and work within those limits.

### Can I use VMware instead of VirtualBox?
Yes. VMware Workstation Player is free for personal use and works well. This manual uses VirtualBox because it's widely accessible and open-source.

### Is it legal to hack Metasploitable or other targets?
Yes, as long as you're doing it in your own isolated lab environment and not targeting any external or production systems.

### Do I need internet access for my lab?
Internet is helpful for downloading tools and updates, but your actual lab environment (especially target systems like Metasploitable) should stay offline for safety.

### What if I break something?
That's part of the learning process. Take snapshots in VirtualBox so you can restore your system to a known-good state quickly.

### Can I expand my lab with Windows servers or other operating systems?
Yes. As your skills grow, you can add Windows Server, Active Directory, Linux servers, or even simulate an enterprise network.

---

## AI Statement
This manual was written by Benjamin Graydon for ENC 4265 using a combination of personal experience and digital assistance. The following tools were used during the creation process:

- **Spellcheck**: built into Google Docs and Microsoft Word.
- **ChatGPT model 4o**: used to help organize structure, rephrase explanations, and generate sample command syntax.

All final content, instructions, formatting, screenshots, and testing were reviewed and authored by the student. AI suggestions were treated as writing support, similar to using a tutor or editor, and not as a replacement for original work.

The manual reflects personal effort, practical testing, and manual Markdown formatting. No generative content was used without human revision and verification.

---

## References

- [draw.io](https://app.diagrams.net/)
- [Nmap Network Scanning](https://nmap.org/book/)
- [Kali Linux – Offensive Security](https://www.kali.org/)
- [Greenbone Vulnerability Management – OpenVAS](https://www.greenbone.net/en/)
- [pfSense Documentation – Netgate](https://docs.netgate.com/pfsense/en/latest/)
- [Metasploitable – Rapid7 on SourceForge](https://sourceforge.net/projects/metasploitable/)
- [VirtualBox User Manual – Oracle](https://www.virtualbox.org/wiki/Documentation)
- [Wireshark – Wireshark Foundation](https://www.wireshark.org/)

All images, tools, and software referenced in this manual are publicly available, used legally and ethically within a home test environment.

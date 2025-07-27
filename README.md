# ARP-Spoofing-CredentialSniffing-Wireshark
ARP Spoofing and Credential Sniffing using Wireshark &amp; Altoro Mutual
🔍 Overview
This project demonstrates how attackers can perform Man-in-the-Middle (MITM) attacks using ARP spoofing to intercept credentials in an insecure network. The target application is Altoro Mutual, a deliberately vulnerable banking site used for ethical hacking practice.

🧰 Tools & Technologies

Parrot  Linux (Attacker machine)

Altoro Mutual VM (Victim machine – intentionally vulnerable website)

arpspoof (Part of dsniff package)

Wireshark (Packet analysis tool)

Ettercap (optional alternative for ARP spoofing)

LAN/Bridge Adapter Network

⚙️ Steps Performed
Network Setup:

Both attacker and victim were connected on the same local network.

##step 1

Verified IP addresses using ifconfig and ip a.

ARP Spoofing Execution:

Enabled IP forwarding:

bash
Copy
Edit

##step 2

echo 1 > /proc/sys/net/ipv4/ip_forward
Launched ARP spoofing using arpspoof:

bash
Copy
Edit

##step 3

sudo arpspoof -t  192.168.0.120  192.168.0.1  &&  arpspoof -t  192.168.0.1  192.168.0.120

This redirected traffic between victim and gateway through the attacker.

##step 4

Traffic Capture with Wireshark:

Started Wireshark and filtered HTTP traffic using:

nginx
Copy
Edit
http
Waited for the victim to log in to the Altoro Mutual site.

##step 5

Credential Sniffing:

Captured login request and extracted username/password from the HTTP POST packet.

Since the site uses HTTP (no SSL/TLS), credentials were in plain text.


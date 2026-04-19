# Cisco-Packet-Tracer-project

🟦 Ⅰ. LAN CONFIGURATION — Router R1 

🔧1 - On R1 (CLI)

enable

configure terminal

👉 2 - Configure G0/0 (LAN side)

interface g0/0

ip address 192.168.1.1 255.255.255.0

no shutdown

exit

🖥️ 3 - PC1 configuration (important)


Go to:

PC1 → Desktop → IP Configuration


IP Address: 192.168.1.10

Subnet Mask: 255.255.255.0

Default Gateway: 192.168.1.1

🔌 Switch1


❌ No configuration needed (default works)


🟩 Ⅱ. LAN CONFIGURATION — R2 (DO SAME)


On Router R2:


interface g0/0

ip address 192.168.2.1 255.255.255.0

no shutdown

exit


PC2:


IP: 192.168.2.10

Gateway: 192.168.2.1

🟨 Ⅲ. LAN CONFIGURATION — R3 (DO SAME)


On Router R3:


interface g0/0

ip address 192.168.3.1 255.255.255.0

no shutdown

exit


PC3:


IP: 192.168.3.10

Gateway: 192.168.3.1

🔗 Ⅳ. WAN CONNECTIONS BETWEEN ROUTERS

🌐 R1 ↔ R2


R1: 10.10.10.1

R2: 10.10.10.2

Mask: 255.255.255.252

On R1:

interface s0/0/0


ip address 10.10.10.1 255.255.255.252
no shutdown

exit


On R2:

interface s0/0/0

ip address 10.10.10.2 255.255.255.252

no shutdown

exit

🌐 R2 ↔ R3

R2: 10.10.11.1

R3: 10.10.11.2

Mask: 255.255.255.252

On R2:

interface s0/0/1

ip address 10.10.11.1 255.255.255.252

no shutdown

exit

On R3:

interface s0/0/0

ip address 10.10.11.2 255.255.255.252

no shutdown

exit

🚀 Ⅴ. ROUTING (THIS IS THE MOST IMPORTANT PART)


Without this → NO PING will work ❌


We use static routing


🟦 Router R1 routes

ip route 192.168.2.0 255.255.255.0 10.10.10.2

ip route 192.168.3.0 255.255.255.0 10.10.10.2

ip route 10.10.11.0 255.255.255.252 10.10.10.2

🟩 Router R2 routes

ip route 192.168.1.0 255.255.255.0 10.10.10.1

ip route 192.168.3.0 255.255.255.0 10.10.11.2

🟨 Router R3 routes

ip route 192.168.1.0 255.255.255.0 10.10.11.1

ip route 192.168.2.0 255.255.255.0 10.10.11.1

ip route 10.10.10.0 255.255.255.252 10.10.11.1

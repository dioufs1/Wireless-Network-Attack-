<h1>(WiFi) Network Attack: Intrusion, Reconnaissance, Monitoring</h1>

<h2>Project Overview</h2>
<p>
In this project, I will be demonstrating a network attack on my home WiFi. The intruder will find my network, gain access, scan my local devices, and start tapping the outbound traffic of a target device through ARP Poisoning.
</p>

<h2>Setup</h2>
<p>For this project, I will be using Parrot OS combined with a network adapter and the tools below:</p>
<ul>
<li>airodump-ng</li>
<li>aireplay-ng</li>
<li>hashcat</li>
<li>nmap</li>
<li>ettercap</li>
<li>wireshark</li>
</ul>

<h2>Reconnaissance</h2>
<ul>
<li>Set the adapter in monitor mode and use airodump-ng to monitor networks within range.</li>
<li>Target a network and get its BSSID and operating channel.</li>
<li>Use airodump to associate clients with a given access point, get the client MAC address, and start collecting their network traffic.</li>
</ul>
<img src="https://i.imgur.com/qrDvzaQ.png" alt="Screenshot 1">
<img src="https://i.imgur.com/VQRQJR6.png" alt="Screenshot 2">
<img src="https://i.imgur.com/T5nzAaE.png" alt="Screenshot 3">

<h2>De-authentication Attack</h2>
<ul>
<li>Use aireplay-ng to target a client and send deauthentication packets to disassociate them with the AP, knocking them off the network.</li>
</ul>
<img src="https://i.imgur.com/rlAJrdr.png" alt="Screenshot 4">
<img src="https://i.imgur.com/tdndleE.png" alt="Screenshot 5">

<h2>Capture EAPOL Handshake</h2>
<ul>
<li>As the device reconnects to its trusted network, airodump will capture the WPA handshake between the client and the AP.</li>
<li>Verify all parts of the EAPOL message in Wireshark.</li>
</ul>
<img src="https://i.imgur.com/yg5fLZC.png" alt="Screenshot 6">
<img src="https://i.imgur.com/zzNhmDr.png" alt="Screenshot 7">

<h2>Hashcat Password Attack</h2>
<ul>
<li>Convert the captured handshake file to be used with Hashcat.</li>
<li>Use a dictionary attack with a well-known wordlist like 'rockyou', combined with a rule list 'best64'.</li>
<li>Weak or previously breached passwords will be cracked and written out with the associated hash.</li>
</ul>
<img src="https://i.imgur.com/jsAh2Fc.png" alt="Screenshot 8">
<img src="https://i.imgur.com/phLetsV.png" alt="Screenshot 9">

<h2>Reconnaissance</h2>
<ul>
<li>Access the network with the cracked password.</li>
<li>Run <code>ifconfig</code> to get the local IP and use <code>nmap</code> to scan the network.</li>
<li>Nmap can be used to scan for vulnerabilities, scan hosts, and choose a weak target.</li>
</ul>
<img src="https://i.imgur.com/sUnnahC.png" alt="Screenshot 10">

<h2>ARP Poisoning & Man-in-the-Middle Attack</h2>
<ul>
<li>Use Ettercap to create a man-in-the-middle attack.</li>
<li>The attacker will sit between the router and the client, secretly forwarding and capturing the traffic.</li>
</ul>
<img src="https://i.imgur.com/uoIb0h8.png" alt="Screenshot 11">

<h2>Packet Analysis</h2>
<ul>
<li>Wireshark can be used for detailed packet capture and analysis.</li>
<li>Online tools can be used to analyze .pcap files for ease of use.</li>
</ul>
<img src="https://i.imgur.com/GhGU7Du.png" alt="Screenshot 12">
<img src="https://i.imgur.com/6mkMJa3.png" alt="Screenshot 13">
<img src="https://i.imgur.com/nnVo1kj.png" alt="Screenshot 14">

<p><b>Disclaimer:</b> This project is for educational purposes only. Unauthorized access to networks is illegal.</p>

 # WebStrike - Network Forensics Investigation

# Scenario
Analysis of a suspicious web server intrusion using network traffic forensics to identify the attacker's origin, tools, and data exfiltration attempts.
  Source: This lab is available at https://cyberdefenders.org/blueteam-ctf-challenges/webstrike/

# Investigation Findings
* Attacker Identification: Traced the malicious activity to IP address `117.11.88.124` originating from a remote location.
* Infiltration Method: Identified the upload of a malicious PHP web shell disguised as an image file (`image.jpg.php`) via an HTTP POST request.
* User-Agent Analysis: Captured the attacker's environment details through HTTP GET request headers.
* Malicious Activity: Confirmed the attacker gained access to the server and targeted sensitive system files.
* Data Exfiltration: Detected an attempt to exfiltrate the `/etc/passwd` file over port `8080`.

# Tools & Techniques
* Network Analysis: Wireshark (TCP/HTTP stream following).
* Filters Used: `http.request.method`, `tcp.dstport`, and `http.request.uri`.

---
> For the full step-by-step solution and specific Wireshark filters, please refer to the [WebStrike Lab.md](./WebStrike%20Lab.md) file.


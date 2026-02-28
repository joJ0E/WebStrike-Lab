# Scenario
- A suspicious file was identified on a company web server, raising alarms within the intranet. The Development team flagged the anomaly, suspecting potential malicious activity. To address the issue, the network team captured critical network traffic and prepared a PCAP file for review.
# Tools used
- wireshark
# Solve steps
- first we found the malicious IP: 117.11.88.124 
- we paste is in website ipgeolocation.io to know From which city did the attack originate
- then we had to know the user-agent of the attacker by allowing the filter http.request.method == GET
- right click on any traffic and go to follow http stream and look at user-agent header
- now we need to know  What is the name of the malicious web shell that was successfully uploaded
- first we allowed the filter http.request.method == POST and  follow the http stream of the traffic we got 
- we found in content-disposition an uploaded file called image.jpg.php so thats our malicious web shell
- we can see the port that the attacker used to upload the file on port 8080
- we also can know where the attacker uploaded it using the filter http.request.uri contains "image.jpg.php"
- last thing we need is to know Which file was the attacker attempting to exfiltrate
- first we apply the filter tcp.dstport == 8080 and follow the tcp stream we can see the curl -X POST -d /etc/passwd
- so the answer is passwd





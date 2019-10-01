# Network Basic

Goal: Analyse a PCAP containing a brute force attempt to find the password that was successful in logging into an admin account.

- Brief tells use that the PCAP contains traffic capturing a brute force attempt against the admin login of a website.
- Download the PCAP file, and open it in wireshark.
- Since this capture involves brute forcing a web login, start filtering by http in wireshark.
- Sort the returned list of http packets by the status code and look for a status code of 200, which indicated that a login was successful.
- After highlighting the correct packet, sort the list by time each packet was sent.
- The request send in the packet before the 200 status code packet should contain the login details for admin.
- Found the credentials, which should be admin:Mellon.

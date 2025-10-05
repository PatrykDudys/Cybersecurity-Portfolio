Analysis / Report of tcpdump logs

As a part of trhe DNS protocol, the UDP protocol was used to contact the DNS server to retrieve the IP address for the domain name of the
hypothetical website "yummyrecipesforme.com". The ICMP protocol was then used to respond with an error message indicating a problem with connecting to the DNS server.
The UDP message going from your browser to the DNS server is displayed in the first two lines of every log event. The ICMP error response from the DNS server to
your browser is shown in each third and fourth lines of the log events with the error message "udp port 53 unreachable". As port 53 is typically 
associated with DNS protocol traffic, we can tell that this is an issue with the DNS server. Issues with performing the DNS protocol 
are further evident due to the plus sign after the query identification number 35084 which indicates flags with the UDP message, and the "A?" symbol indicates flags with 
performing the DNS protocol. The ICMP protocol error message about port 53 highly indicates that there is a problem with the DNS server/it 
isn't responding, as well as the flags associated with the UDP message and domain name retrieveal which further reinforce that the DNS server is not responding.

The incident ocurred today 1:24pm. Customers were presented with the message "destination port unreachable", whilst trying to reach the website, which they mentioned to the organization. 
In our investigation, we used a packet sniffer (tcpdump) which made it highly evident that port 53 was unreachable.
Possible causes include a firewall which is blocking UDP traffic, the server potentially being down or another network device such as a router may be blocking the UDP port. 
Another cause can include a possible malicious attack such as a DoS attack since ICMP protocol messages are often seen in response
to scanning or blocking malicious traffic.


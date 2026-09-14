# Windows DNS Troubleshooting Lab
## Objective
The goal of this project was to demonstrate a DNS issue within of a windows 11 VM and use the command line to troubleshoot and resolve it. 
## Environment & Tools
- The purpose of using Oracle VirtualBox was to create a Windows 11 virtual machine to simulated a user environment experiencing a DNS issue.
- Windows 11 VM-Used to simulate a user's computer environment having DNS issue in a isolated environment to demonstrate command line network skills. 
 - ipconfig (ipconfig /all)  to display our user computer network configuration to view IPv4 address, subnet mask, Default gateway, DHCP, DNS server.
- ping to test if our user computer can reach a destination over the network and measure whether packets receive replies
- nslookup to verify that DNS can resolve a domain name to an IP address
- ## Troubleshooting Process
- A user has reported they can't reach google.com or any other websites.
- The first thing I checked was the computer network configuration in the command line using the command ipconfig /all
- To verfiy it has a valid IP address, gateway, and DNS server.
- We ping a known address 8.8.8.8 to verify we can send and receive packets and replies over the network
-   From the test we gotten 4 packets sent and 4 packets received, o packets lost. Indicating internet connection is working
-   The issue at this point could indicate a DNS issue
-   Next we use nslookup google.com to see  DNS can resolve a domain name to an Ip address that is well known
-   nslookup results were DNS request timed out, server unknown , Address 10.0.2.99
-  I first checked Ethernet adapter's IPv4 settings to determine whether DNS server address had been statically configured, which could have caused the DNS resolve issue with domains 
 - I  check the device ethernet properties section then into its IPv4 radio button into DNS settings I have changed DNS back to Obtain DNS server address automictically. This way the system can resolve DNS properly on the network. 
-   Opening the command line to run ipconfig /flushdns to clears the computer DNS resolver cache.
-   Testing DNS again with nslookup with the domain of microsoft.com. Resulted in a successful returned IP address 
  ## Resolution
  In the DNS server configuration I changed the static configuration of DNS server address to obtain DNS server address to automictic instead of static configured.
  I then went back into the command line to run the command ipconfig /flushdns to clear the DNS cache.
  I verify the changes by using nslookup to microsoft.com to see if DNS was able to resolve the domain name to a IP address 
  ## verification 
  nslookup results back with Name microsoft.com address 150.171.109.72 which does confirm DNS is able to resolve domain names.

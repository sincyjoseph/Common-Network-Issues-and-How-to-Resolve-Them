# Common-Network-Issues-and-How-to-Resolve-Them

Networks are networks. Despite best efforts to keep things smooth all the time every day, things happen. Here's a look at some common network issues, some tips for quickly resolving them, and even better, how to prevent them from occurring again.

# 1. Duplicate IP Addresses
When two devices attempt to share a single IP, you see the dreaded "Address Already in Use" Kill — with no ability to access the network.

**The Quick Fix:** The blame for this often rests with your router's default DHCP configuration. DHCP is probably trying to assign your new device an address at the beginning of your subnet, and another device may already occupy these low-numbered addresses with static IPs. If you've just introduced a new device or server to your network, it may have its own DHCP server. Simply disable the DHCP server on that device to restore sanity to your network.

**The Preventive Measure:** You can take one simple step to avoid IP conflicts by modifying your router's configuration to begin assigning DHCP addresses near the top end of your subnet, leaving the lower addresses available for devices that require static IPs.

# 2. IP Address Exhaustion
To troubleshoot this issue, use the ipconfig command. If the workstation has assigned itself an IP address that begins with 169.x.x.x, it means that no IP address was available from the DHCP server.

**The Quick Fix:** Some users on cable internet might not have a local router, in which case IP addresses are assigned on a limited basis directly from your ISP. You have probably run out of allowed IP addresses from your ISP. The solution to this is to purchase either a standalone router or WiFi access point with an integrated router. This creates your own local pool of internal addresses, ensuring you won't run out.

If you already have a local router with DHCP, the default address pool might be too small for your network. By accessing the DHCP settings on the router, you can adjust the size of the address pool to meet your network's needs.

**The Preventive Measure:** It's important that any internet-connected network have a local router in operation with NAT and DHCP, both for security reasons and to prevent IP address exhaustion. The router needs to be the only device connected to the modem, with all other devices connecting through the router.


# 3. DNS Problems
Errors such as The Network Path Cannot Be Found, IP Address Could Not Be Found, or DNS Name Does Not Exist, can usually be traced to a DNS configuration issue. The command line utility nslookup can be used to quickly show a workstation's DNS settings.

**The Quick Fix:** Workstations and other network devices can be configured to use their own DNS servers, ignoring the server assigned by DHCP. Checking the 'Internet Protocol Version 4 (TCP/IP)' settings for your adapter will show if an incorrect DNS server is specified, so just select "Obtain DNS server address automatically" instead.

**The Prevention Measure:** Your local router might be configured to operate as a DNS Server, creating a DNS pass-through to your ISPs servers. On busy networks, this may overload the capabilities of the router. Change your network's DHCP settings to directly access your DNS servers.

# 4. Single Workstation Unable to Connect to the Network
If only a single workstation is displaying the "No internet" message when opening a web browser, we can usually assume that the rest of the network is healthy and turn our attention to any hardware and software that is particular to this system.

**The Quick Fix:** To resolve this network issue, start by eliminating the obvious communication barriers such as a bad cable, poor WiFi signal, failing network card or incorrect drivers. Ensure that the workstation's network adapter is configured with the correct IP, subnet, and DNS servers.

If that doesn't solve the problem, check any firewall software on the device to ensure that necessary ports are open to the external network. Common ports include 80 and 443 for web traffic, plus 25, 587, 465, 110, and 995 for email.

**The Preventive Measure:** It's usually best to leave all workstation TCP/IP settings to "Automatically assigned." Use a DHCP server to hand out a uniform configuration to all devices on the network. If a static IP is needed on a particular workstation or server, most DHCP servers allow the ability to create static IP mappings.

# 5. Unable to Connect to Local File or Printer Shares
Sharing problems are among the most difficult network problems to solve, due to the number of components that need to be configured properly.

Most commonly, sharing problems arise due to conflicts between mixed security environments. Even different versions of the same operating system sometimes use slightly different security models, which can make interconnection of workstations difficult.

**The Quick Fix:** We can cure sharing problems most efficiently by drilling down through the possibilities in this order:

1. Ensure that the required services are running. On Windows systems, the server, TCP/IP NetBIOS Helper, workstation, and computer browser services all need to be running. On Linux machines, Samba is the primary component required to share with Windows systems.
2. Check your firewall(s). It's very common for a workstation's firewall to be configured to block file and printer sharing traffic, especially if a new antivirus package is installed that introduces its own firewall. Firewall issues can also exist at the hardware level, so ensure that routers or managed switches are passing share traffic within the subnet. Speaking of subnet….
3. Ensure all workstations are on the same subnet. This problem typically only appears on complex networks, however, even simple networks sometimes have static-IP equipment with an improperly configured subnet. The result is that external traffic will move about just fine, while internal traffic will hit unexpected roadblocks.
4. All Windows network adapters will need File and Printer Sharing for Microsoft Networks, Client for Microsoft Networks, and NetBIOS over TCP/IP enabled.
5. Once the above checks have passed, it's finally time to check the most likely culprit, permissions. There are multiple layers of access required, each with their own interface within the OS. Check for:
- Systems configured with the wrong workgroup or domain.
- Incorrectly configured HomeGroup.
- Network type set to Public.
- Incorrect NTFS permissions.

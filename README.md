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

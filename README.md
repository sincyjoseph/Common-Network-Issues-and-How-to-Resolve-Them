# Common-Network-Issues-and-How-to-Resolve-Them

Networks are networks. Despite best efforts to keep things smooth all the time every day, things happen. Here's a look at some common network issues, some tips for quickly resolving them, and even better, how to prevent them from occurring again.

# 1. Duplicate IP Addresses
When two devices attempt to share a single IP, you see the dreaded "Address Already in Use" Kill — with no ability to access the network.

**The Quick Fix:** The blame for this often rests with your router's default DHCP configuration. DHCP is probably trying to assign your new device an address at the beginning of your subnet, and another device may already occupy these low-numbered addresses with static IPs. If you've just introduced a new device or server to your network, it may have its own DHCP server. Simply disable the DHCP server on that device to restore sanity to your network.

**The Preventive Measure:** You can take one simple step to avoid IP conflicts by modifying your router's configuration to begin assigning DHCP addresses near the top end of your subnet, leaving the lower addresses available for devices that require static IPs.

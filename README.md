# Minecraft DoS Patches
> Patches that prevent malicious Minecraft plugins from saturating host internet resources for DDoS. In recent events, Minecraft servers (containerized using services like Multicraft or Pterodactyl) have been used to conduct attacks as part of a botnet.

# What is the root issue?
Often times, the software hosting providers use rely on docker for containerization. This results in a virtual interface being created for each "server", which has access to the physical devices full internet capacity. This allows the bad actor(s) to send bulk traffic to a remote victim host.

# What is the solution?
It is best practice to prevent a single customer from saturating network resources (in a shared hosting environment). This can be done by adjusting the virtual network interface created by docker to something less than the full-network speed (i.e., 10/100). This prevents single clients from consuming all resources, however, does not prevent the attacks as a whole.

Second to this, it would be best to implement some form of JAR scanning software, ensuring what client(s) are uploading is not malicious.

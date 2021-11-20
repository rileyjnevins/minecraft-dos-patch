# Pterodactyl (Wings) Botnet Patch
> This specific patch applies to the Pterodactyl panel. Pterodactyl uses docker to create containers for new servers. A feature this panel lacks is the ability to limit network capabilities, like they do CPU and memory. Bad actors can take advantage of this in a shared hosting environment for DDoS attacks.

> This patch adjusts wings docker 'power.go' file to identify customer virtual interfaces, from there we limit their network abilities. This does not prevent denial of service, it limits the severity. 

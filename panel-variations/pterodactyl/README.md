# Pterodactyl (Wings) Botnet Patch
> This specific patch applies to the Pterodactyl panel. Pterodactyl uses docker to create containers for new servers. A feature this panel lacks is the ability to limit network capabilities, like they do CPU and memory. Bad actors can take advantage of this in a shared hosting environment for DDoS attacks.

> This patch adjusts several files to identify virtual interfaces of containers. We can then apply traffic shaping rules (specifically token bucket filters) to limit the input and output of this container based on limits defined in the server's build configuration on the panel. While this does not inherently prevent denial of service, it limits the severity.



<h2>Configuration</h2>

This program does require a few changes to both wings and the panel to function. However, these tasks should be easy to do with base and updated versions of Pterodactyl. The following steps will require you to have a Pterodactyl environment that is already setup and working correctly.



<h3>Building Wings</h3>

For this, [Go](https://go.dev/doc/install) is required on the **Linux** machine you're going to be building Wings on. There is no documented version of Go for this task however the latest version is recommended.



First of all, you'll need to clone the upstream [Wings](https://github.com/Pterodactyl/Wings) repository. Once cloned, you will then need to replace some of the original Wings files with the custom files in the [wings](./wings) folder of this repo. Once done, run the following command:

`go build`

Which will build an executable named wings in the base directory of the Wings repository. If it's done successfully, you can then move the newly created wings executable into the `/usr/local/bin` directory.



From here you can run the following command for the changes to take effect.

`systemctl restart wings`


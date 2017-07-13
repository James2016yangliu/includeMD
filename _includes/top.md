
## Summary

OpenECOMP 1.0.0 represents a complete demo platform with two service examples as contributed by AT&T to the Linux Foundation ONAP project.

## Repository Links
- Docker Containers
- Platform and Demo Service Artifacts
- Source


## Installation Instructions
BasicOpenECOMP installation instructions are available as a README.md file. Step by step tutorials for setting up a Rackspace account, using the portal, designing services, and instantiating services are provided here.

## Interacting with VMs and Containers
 
 All VMs created have 2 network interfaces. One is public and visible to the Internet (eth0) the other is on a private 10.0.0.0/8 network (eth1). The public IPs are being used for user log in and remote management whereas the 10.0.0.0/8 addresses are used for all internal ONAP communication. This allows pre-configuration of DNS names, certificates and IP addresses within the individual components. It also allows spin up with multiple ONAP instances within one Rackspace tenant without conflict.
<br />
For example if the public IP address for a VM is 1.2.3.4 and the private key matching the public key from the heat template is stored in a file of the name openecomp_key you can log into the VM with:
``` javascript
ssh –i path/to/openecomp_key root@1.2.3.4
```
 Please note that we do not provide any public/private key pair to access ONAP VMs. That key pair will be created and uploaded by users, as explained in the README.md file and tutorial.
<br />
 Inside the VM you can list thedockercontainers by typing:
 ``` javascript
docker ps
```

and can get a shell prompt by executing the bash command.
<br />
For example:
``` javascript
root@vm1-robot:~# docker ps
   CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS              PORTS                NAMES
   129725d30b7f        ecomp-nexus:51215/openecompete   "lighttpd -D -f /etc/"   3 minutes ago       Up 3 minutes        0.0.0.0:88->88/tcp   openecompete_container
   root@vm1-robot:~# docker exec -it openecompete_container bash
   root@e37dde66316e:/#
```

Please note that this configuration is for demo purposes only. For a real productiondeploymenta more secure network, certificate and key design would be used.
## VMs and Containers
Additional information about VMs and containers are provided below
 
### DCAE






 
 
 
 
 
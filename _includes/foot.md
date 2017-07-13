
 
 ## Known Restrictions
 
### General:
- This release is not for production use out of the box since it is not configured for any auto-scaling(healing as in min=1, max=1), resiliency, scalability, clustering, disaster recovery capabilities neither any persistency after a VM and/or container is rebooted
- User can install without Docker but no documentation has been provided in this release.
- HEAT templates apply to Rackspace and OpenStack environments only. Consult Rackspace documentation to get memory, vCPU for other openstack image sizes
- Startup sequence is critical since the DMaaP Message Router (MR) and its topics must be in place before flows will work
- The messaging topics used by the OpenECOMP components have already been pre-configured into DMaaP Message Router initialization state.  However, it is advised to leave sufficient time in the system startup sequence for the Message Router to complete its booting (e.g. ~20 seconds) before proceeding with launching of OpenECOMP components that depend on Message Router for communications.
- Healthcheck details can provide information on sub-component issues in many cases
- Rackspace monitoring of VM’s is first level of VM health then robot framework health check.
- Healthcheck can be used for monitoring key components like DMaaP MR (including the list topics command)
- Additional application monitoring (e.g., key log files and alarms) will be documented in future.
- Application monitoring tools are not included in this release. 

### AAI:
- The hbase configuration is for a demo use case only – it should be configured as per application needs.

### APPC:
- The APPC LCM APIs (appc-provider-lcm) only work when there is an AAI instance available and set up to interface with APPC
- Currently, the "ModifyConfig" API and the implementation in the Master Directed Graph is only designed to work with the vFW Closed-Loop Demo.
- The “appc-iaas-adapter” is not starting automatically during Docker instantiation.
- A maven settings script (which lets APPC know where to download/upload maven artifacts to/from) needs to be provided if building the project on a local machine. An example to set up a settings script can be found here: https://maven.apache.org/settings.html
- see example root pom
### Portal:
- Portal depends on DNS names to access the landing page login URL. So this requires manual setup of DNS host details in system.properties file as detailed in the instructions
### MSO:
- Although MSO should run on any cloud integrated with Openstack (i.e. Icehouse), it has only been validated on Rackspace
### Robot Framework:
- Robot container does not contain any persistent volumes, results should be stored and viewed elsewhere 
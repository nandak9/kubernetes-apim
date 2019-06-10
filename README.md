# Kubernetes and Helm Resources for WSO2 API Manager

## Deploy Kubernetes resources 

In order to deploy Kubernetes resources for each deployment pattern, follow the **Quick Start Guide**s for each deployment pattern
given below:

* [WSO2 API Manager pattern 1](pattern-1/README.md)

* [WSO2 API Manager pattern 2](pattern-2/README.md)


## How to update configurations

Kubernetes resources for WSO2 products use Kubernetes [ConfigMaps](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)
to pass on the minimum set of configurations required to setup a product deployment pattern.

For example, the minimum set of configurations required to setup pattern 1 of WSO2 API Manager can be found
in `<KUBERNETES_HOME>/pattern-1/confs` directory. The Kubernetes ConfigMaps are generated from these files.

If you intend to pass on any additional files with configuration changes, third-party libraries, OSGi bundles and security
related artifacts to the Kubernetes cluster, you may mount the desired content to `/home/wso2carbon/wso2-server-volume` directory path within
a WSO2 product Docker container.

The following example depicts how this can be achieved when passing additional configurations to WSO2 API Manager in pattern 1 of WSO2 API Manager:

a. In order to apply the updated configurations, WSO2 product server instances need to be restarted. Hence, un-deploy all the Kubernetes resources
corresponding to the product deployment, if they are already deployed.

b. Create and export a directory within the NFS server instance.
   
c. Add the additional configuration files, third-party libraries, OSGi bundles and security related artifacts, into appropriate
folders matching that of the relevant WSO2 product home folder structure, within the previously created directory.

d. Grant ownership to `wso2carbon` user and `wso2` group, for the directory created in step (b).
      
   ```
   sudo chown -R wso2carbon:wso2 <directory_name>
   ```
      
e. Grant read-write-execute permissions to the `wso2carbon` user, for the directory created in step (b).
      
   ```
   chmod -R 700 <directory_name>
   ```

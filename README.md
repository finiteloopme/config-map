# Configuration management and Code promotion

### Date: 10-July-2017

# Why Config Management

1. There is a need to **externalise application configuration** as this will probably be different per environment or per deployment
2. To every deployment to have **different values for runtime configuration**
3. Store config in the environment [12factor](https://12factor.net/config)

## Deploying an application not a container
A developer is deploying **An Application** not a container.  This application can be composed of multiple containers.  So configuration per deployment needs to addressed at application level and not individual containers.

## ConfigMap
All the configuration used/needed per application should be centralised, so that changes in configuration will not impact the definition of the deployment. This is what ConfigMap is for.

In simplistic terms, configuration can be broadly categorised as:
1. Config file (e.g. properties files)
2. Command line arguments
3. Environment variables

# Secrets
Secrets behave as encoded-64 configmaps. From a security perspective, they have the following **limitations** (as of release 3.5):

1. They are not encrypted at rest.
2. By default, cluster admins can see all the secrets of all the tenants.
3. When in use (i.e. mounted as tempfs in the node that runs the pod that is using them), they can be seen by a node administrator.
4. When in use, they can be seen by anyone who has the ability to remote shell into the container.

> Look at `Integration with Vault` in references to externalise secretes management

# Reference

Name | URL
- | -
Configuring Application | https://blog.openshift.com/configuring-your-application-part-1/
Configuration with Application Promotion | https://blog.openshift.com/configuring-your-application-part-2/
Integration with Vault | https://blog.openshift.com/managing-secrets-openshift-vault-integration/
Environment dependent properties management | https://blog.openshift.com/environment-dependent-property-management-strategies-openshift-pipelines/
Promoting applications across environments | https://blog.openshift.com/promoting-applications-across-environments/

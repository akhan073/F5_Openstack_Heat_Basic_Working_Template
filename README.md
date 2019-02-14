
## Introduction
 
Welcome to the GitHub repository of akhan073 Tested F5's Heat Orchestration Templates for deploying F5 BIG-IP Virtual Edition in Newton OpenStack environments (any Openstack Distribution).  

## Template information

This Template has got four YAML file as Below:
 - f5_ve_standalone_3_nic.yaml - `This Template is the Master Template and deploys a standard f5 standalone VE.`
 - heat_template_test.yaml - `This Template Setup infrastructure for testing F5 Heat Templates.`
 - heat_template_test_environment.yaml - `This is the environment file (caution : please update this master file carefully as per the existing environment).`
 - heat_template_test_networks.yaml - `This Template Create the four networks needed for the heat plugin tests along with their subnets and connect them to the testlab router.`

 **NOTE:** This Template is build to have an offline deployment, If you require to orchestrate the Installation, Configuration and Provisioning of the BIG-IP VE then please make use of https://github.com/F5Networks/f5-openstack-hot


## Supported Versions

### BIG-IP VE
The templates are developed for standard BIG-IP Virtual Edition images version **13.0 or later**.
Earlier versions may require image patching to create OpenStack-ready images in *glance*.
**Note:**
Refer to [f5-openstack-heat](https://github.com/F5Networks/f5-openstack-heat) for templates that launch pre-version 13.0 instances.

### OpenStack
The templates are working fine on an operational OpenStack Newton deployment. (This can be tested with other OpenStack versions as well)
`For additional resources on configuring environments with F5 Integration for OpenStack, refer to this [configuration guide](http://clouddocs.f5.com)`

## Prerequisites
The following is a summary of prerequisites for successfully launching templates from this repo:
  - Neutron Components:
    - Management network and subnet (where management UI can be accessed)
    - External network and subnet (where floating IP resides)
    - Additional network(s) and subnet(s) (e.g. Data Subnet)
    - Corresponding router(s) configuration
    - Security group configuration that can be attached.
  - Nova Components:
    - Need to Configure the Key pair for SSH access to BIG-IP VE
  - Glance Components:
    - BIG-IP Virtual Edition Image Version 13.0 or later added to Images. The image file must be in qcow.zip format and can be any size (ALL, LTM, or LTM_1SLOT).
  - Openstack Client CLI.

## Launching Stacks

1. Ensure the prerequisites are configured in your environment. See README from this project's root folder.
2. Clone this repository or manually download the contents (zip/tar). As the templates use nested stacks and referenced components, we recommend you retain the project structure as-is for ease of deployment. If any of the files changed location, make sure that the corresponding paths are updated in the environment files.
3. Locate and update the environment file (**_env.yaml**) with the appropriate parameter values. Note that some default values are used if no value is specified for an optional parameter.
4. Launch the stack using the OpenStack CLI with a command using the following syntax:

### CLI Syntax

`openstack stack create <stackname> -t <path-to-template> -e <path-to-env>`

# Ansible and DNA Center Together Forever
Collateral for the AnsibleFest 2019 Presentation

## Installation Instructions
Obtaining all of the necessary collateral demonstrated follow these steps:

1. clone the **ansiblefest_2019** repository
   ```shell
   git clone --recursive https://github.com/jandiorio/ansiblefest_2019
   ```
   This repository contains two additional submodules: the Cisco DNA Center modules and the Cisco DNA Center Inventory Plugin.  
2.  Run the `install.yml` to complete the installation. 
```shell
ansible-playbook -i localhost installation/install.yml
```

The `install.yml` perfoms the following steps: 

1. Create Links to Modules in `playbooks/library` directory
2. Create `module_utils/network/dnac` directory
3. Create `__init__.py` in the directory created
4. Copy dnac.py to `module_utils/network/dnac`
5. Install Dependent Python Package - timezonefinder
6. Install Dependent Python Package - geopy

## Demo Instructions

## License
This solution is Copyright (c) 2019 World Wide Technology. All rights reserved. A copy of the applicable end user license agreement for this solution can be obtained by emailing AutomationTeam@wwt.com.

## Author Information
**Jeff Andiorio** - jeff.andiorio@wwt.com
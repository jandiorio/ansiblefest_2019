# AnsibleFest 2019 - Do I choose Ansible, DNA Center or both?
Collateral for the AnsibleFest 2019 Presentation 

[dnac-and-ansible slides](https://github.com/jandiorio/ansiblefest_2019/blob/master/dna-center-and-ansible-draft.pdf)

## Session Information 
AnsibleFest 2019

September 24, 2019 

1:00 - 1:45 EDT

*A PDF of the slides is located in the root of this project*  

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

1. Create a `library` subfolder in `playbooks`
2. Create Links to Modules in `playbooks/library` directory
3. Create `module_utils/network/dnac` directory
4. Create `__init__.py` in the directory created
5. Copy dnac.py to `module_utils/network/dnac`
6. Install Dependent Python Package - timezonefinder
7. Install Dependent Python Package - geopy

## Demo Instructions

The demonstration during the AnsibleFest session used a lab environment in the WWT Advanced Technology Center.  [Network Automation with Ansible + DNA Center Lab](https://www.wwt.com/lab/network-automation-with-ansible-dna-center)

The playbooks were executed in sequence with 2 steps that were performed manually due to the lack of an existing API.  

1. Create Site Hierarchy
2. Discover Network Devices
3. Configure Network Settings
4. Site Role Assignments
5. Add VLANs to Switches
6. Add SVIs to Switches
7. Configure AP Port
8. Create Dummy Wireless Profile 
9. Provision WLC
10. Provision AP - **Manual Step**
11. Create SSID
12. Create New Wireless Profile
13. Add  Wireless Interface - **Manual Step**
14. Provision WLC

The playbooks are named with a numerical prefix indicating the corresponding step from the above list. 
```
    -rw-r--r--  1 root root 2580 Sep 16 14:50 1-create-hierarchy.yml
    -rw-r--r--  1 root root  717 Sep 16 14:50 11-create-wireless-ssid.yml
    -rw-r--r--  1 root root  918 Sep 16 14:50 12-create-wireless-profile.yml
    -rw-r--r--  1 root root  921 Sep 16 14:50 14-provision-wireless.yml
    -rw-r--r--  1 root root 3121 Sep 16 14:50 2-discover-devices.yml
    -rw-r--r--  1 root root 5782 Sep 16 14:50 3-create-network-settings.yml
    -rw-r--r--  1 root root 1468 Sep 16 14:50 4-site-role-assignments.yml
    -rw-r--r--  1 root root  959 Sep 16 14:50 5-declarative_l2_vlans.yml
    -rw-r--r--  1 root root 2109 Sep 16 14:50 6-declarative_l3_interfaces.yml
    -rw-r--r--  1 root root 1077 Sep 16 14:50 7-config-ap-port.yml
    -rw-r--r--  1 root root  735 Sep 16 14:50 8-create-dummy-wireless-profile.yml
    -rw-r--r--  1 root root 1044 Sep 16 14:50 9-provision-wireless.yml
```

Each playbook has a reference to the commandline string to execute: 

    `ansible-playbook -i inventory/hosts.yml playbooks/1-create-hierarchy.yml -e "{'host_groups':'dna_3_dnac','desired_state':'present'}" --ask-vault-pass`

If you are using your own environment some things need to change: 

1. `./inventory/hosts.yml`  needs to change to match your DNA Center environment
2. `./vars/password.yml` needs to reflect the credentials for your environment
3. `./inventory/inventory_plugins/dna_center.yml` needs to change for your environment

If you would like to use our environment, just navigate to [www.wwt.com](https://www.wwt.com) and register for an account.  The link to this environment is at the top of this section.  

## DNA Center Modules 

The modules are installed as a submodule within this project, but if you wanted to pull them directly, you can find them here: 

[DNA Center Modules](https://github.com/jandiorio/ansible-dnac-modules)

## DNA Center Inventory Plugin

The source for the inventory plugin can be found here: 

[DNA Center Inventory Plugin](https://github.com/jandiorio/ansible-dnac-inventory-plugin)

## License
This solution is Copyright (c) 2019 World Wide Technology. All rights reserved. A copy of the applicable end user license agreement for this solution can be obtained by emailing AutomationTeam@wwt.com.

## Author Information
**Jeff Andiorio** - jeff.andiorio@wwt.com
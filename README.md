# three tier app CI/CD for Mizi telecom
- date: 2017.12.25

## Environment
- OSP workstation: workstation.5836.rhpds.opentlc.com
- Prod bastion: bastion.2a2a.example.opentlc.com

## Basic Requirement
- git repository: https://github.com/hatsari/ansible-training.git
- Playbooks to deploy internal 3-tier app
- Install HA Ansible Tower

## Provision QA Environment (Including smoke test)
### Creating Open Stack instances
- preparation to ssh: ssh.cfg is needed to connect to jumpbox so this file can be made by playbook.
- instances: 
  - apps(app1, app2)
  - appdbs(appdb1)
  - frontends(frontend)
- using same playbook, instances can be created or deleted depending on extra variable(dead_or_alive)
### deploying 3tier app

## Provision Production Environment (Including smoke test)
- 3tier apps can be deploy on dev or production switching the tower's inventory

## Ansible Tower Workflow Templates
### Workflow steps
  * initialize ssh connection environment
  * provision instances on openstack
  * deploy 3tier apps and verify the service using in-memory inventory
	* if smoke test failed, destory instances on openstack
  * deploy 3tier apps and verify the service using tower static inventory
    * if smoke test failed, clear 3tier apps 

-----
below is the detailed explaination for each playbook.

- osp_configure_3tier.yml[osp_configure_3tier.yml]
- osp_create_instances.yml
- osp_create_multi_instances.yml
- osp_create_network.yml
- osp_create_security.yml 
- osp_flavor.yml

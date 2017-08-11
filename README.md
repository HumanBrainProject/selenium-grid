# Ansible playbook to install a Selenium Grid


Selenium Grid is easy to setup, most of the problems comes when you try  to  run 
the web browser "headless".  You need to install a virtual frame buffer( xvfb ), 
and you have to tweak the browser settings to get them working.

These web browser settings seems to be quite hightly version dependant


## Prerequisites

VMs running Ubuntu Xenial (16.x LTS)
* user ubuntu with full sudo rights exists
* an SSH key on the machine for the ubuntu user

## Setup

* create a security group selenium for all the VMs
* Create one selenium-grid node VM (master), attach a public IP to this machine
* Create one or more selenium-node VMs (workers)

Put the VMs IP in the hosts.txt file

For the selenium security group
* open TCP port 4444 from the outside world (acces to the selenium grid UI)
* open TCP port 4444 to the selenium group (acces to the API)
* open TCP port 5555 to the selenium group 
 

## Usage

Install the platforms components via Ansible

```
ansible-playbook install_grid.yml -i host.txt
```

Do some clean-up on the nodes after a run (needed sometimes)
```
ansible-playbook cleanup_nodes.yml -i host.txt
```

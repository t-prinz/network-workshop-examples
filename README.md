# Red Hat Ansible Automation Platform - Network Tool Kit

More info coming soon....


# Ansible Network Automation Workshop

This Ansible Network Collection is used in conjunction with the Ansible Network Automation Workshop.  The workshops are instructor-led exercises to teach Ansible Automation.

Please refer to rollowing links for more information and perscriptive exercises:
- The Workshops Landing Page - [https://ansible.github.io/workshops](https://ansible.github.io/workshops)
- The Github Source - [https://www.github.com/ansible/workshops](https://www.github.com/ansible/workshops)

## Network roles

- [network.toolkit.backup](roles/backup/README.md)
- [network.toolkit.banner](roles/banner/README.md)
- [network.toolkit.build_report](roles/build_report/README.md)
- [network.toolkit.facts](roles/facts/README.md)
- [network.toolkit.l3_interface](roles/l3_interface/README.md)
- [network.toolkit.reload](roles/reload/README.md)
- [network.toolkit.restore](roles/restore/README.md)
- [network.toolkit.system](roles/system/README.md)
- [network.toolkit.user](roles/user/README.md)

# Sample inventory

[routers:vars]
ansible_user=ec2-user

[routers:children]
cisco
juniper
arista

[cisco]
rtr1 ansible_host=3.17.78.88 private_ip=172.16.200.186
[arista]
rtr2 ansible_host=3.144.106.81 private_ip=172.18.43.182
rtr4 ansible_host=52.15.213.42 private_ip=172.18.237.32
[juniper]
rtr3 ansible_host=3.15.149.178 private_ip=172.16.244.89

[cisco:vars]
ansible_network_os=ios
ansible_connection=network_cli

[juniper:vars]
ansible_network_os=junos
ansible_connection=netconf

[arista:vars]
ansible_network_os=eos
ansible_connection=network_cli
ansible_become=true
ansible_become_method=enable

[dc1]
rtr1
rtr3

[dc2]
rtr2
rtr4

[control]
ansible-1 ansible_host=18.117.158.14 ansible_user=ec2-user private_ip=172.16.2.57

[network:children]
routers
[network:vars]
restore_inventory="Workshop Inventory"
restore_credential="Workshop Credential"
restore_project="Workshop Project"

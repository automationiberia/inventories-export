# # inventories-export

```yaml
ansible-playbook -i inventory inventory_export.yml  -e '{input_tag: [inventory,inventory_sources,hosts,groups,users,teams]}'
```

```yaml
 tree group_vars/controller/
group_vars/controller/
├── controller_groups.yaml
├── controller_hosts.yaml
└── controller_inventories.yaml
```

```yaml
$ cat group_vars/controller/controller_hosts.yaml
---
controller_hosts:
  - name: aws-instance-group
    description: localhost
    inventory: "Demo Inventory AWS"

  - name: azu-instance-group
    description: localhost
    inventory: "Demo Inventory AZU"

  - name: vm-onprem-instance-group
    description: localhost
    inventory: "Demo Inventory VM_ON_PREM"
```

```yaml
ansible-playbook -i inventory config-controller.yaml --tags hosts -e '{controller_state: absent}'
```

```yaml
ansible-playbook -i inventory config-controller.yaml --tags hosts -e '{controller_state: absent}' -e@'/tmp/filetree_output/Default/inventories/Demo_Inventory/current_hosts.yaml'
```

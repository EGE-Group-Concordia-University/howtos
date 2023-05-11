# Manage virtual machines with VBoxManage

## List exisiing virtual machines
To list defined virtual machines:
```
VBoxManage list vms
```
To list running virtual machines:
```
VBoxManage list runningvms
```

## Starting existing virtual machines
To start a virtumal machne named myvm in headless mode:
```
VBoxManage startvm myvm --type headless
```
## Shuting down a running virtual machine
To shutdown a running virtual machine named myvm:
```
VBoxManage controlvm myvm acpipowerbutton
```

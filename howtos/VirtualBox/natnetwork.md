# Nat networks

## Creation
Nat networks can be created in Files>settings

## Port forwarding
In Files>settings choose your netowrk and click on edit properties.

## Assign a fixed IP to your virtual machine
In an ubuntu machine modify `/etc/netplan/00-installer-config.yaml` to look as follows:
```
network:
  ethernets:
    enp0s3:
      dhcp4: no
      gateway4: 10.0.2.1
      addresses: [10.0.2.12/24]
  version: 2
```
In this example the static IP adress of the virtual machine will be `10.0.2.12`.

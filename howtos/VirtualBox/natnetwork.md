# Nat networks

## Creation
Nat networks can be created in Files>Preferences under Network.

## Port forwarding
In Files>Preferences>Network choose your network and click on edit properties.

## Assign a fixed IP to your virtual machine
In an ubuntu machine modify `/etc/netplan/00-installer-config.yaml` to look as follows:
```
network:
  ethernets:
    enp0s3:
      dhcp4: true
      dhcp4-overrides:
        use-dns: false
      gateway4: 10.0.2.1
      addresses: [10.0.2.13/24]
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
        addresses: [132.205.1.1,132.205.96.93,132.205.96.94]
  version: 2

```
In this example the static IP adress of the virtual machine will be `10.0.2.12`.

Check your configuration with
```
sudo netplan --debug apply
```


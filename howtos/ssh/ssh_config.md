# Example use cases for ```ssh_config```

The behaviour of ```ssh``` can be configured with the global ```/etc/ssh/ssh_config``` configuration file and in the user ```~/.ssh/config``` file.
More infomrmation can be found on the [offical documentation](https://www.ssh.com/academy/ssh/config).

## Connecting to a remote host on a specific port
To connect to a remote host on a specific port one uses typically the command
```
ssh bob@remote.host.com -p 12345
```
This can be simplified by defining the follwing entry in the ```ssh``` config file:
```
Host myremote
    HostName remote.host.com
    User bob
    Port 12345
```
Connection to ```remote.host.com``` can now be done by
```
ssh myremote
```
A typical example is when a remote host is accesible via a previousley defined local port forwarding. Instead of using the command
```
ssh localhost -p 43022
```
one can use
```
ssh remote
```
after adding the follwiong entry in the ```ssh``` config file:
```
Host remote
    HostName localhost
    Port 43022
```

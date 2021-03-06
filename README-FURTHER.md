# Available Options

In order to keep the [parameters](group_vars/all) manageable we defaulted a lot of them.  
Take a look at the [defaults](roles/nodes/defaults/main.yml) to see which other options are available.

## Webserver

You can choose between nginx and apache. There is a config template located at /roles/nodes/templates for both.

```
webserver: "apache"
```

## SSL Decryption

The ssl decryption can be handled by the loadbalancer or the nodes. Default is the loadbalancer.
The two parameters depend on each other, so we probably will merge them at some point. Now one has to be 'yes' and the other 'no'.

```
# decrypt ssl at loadbalancer
ssl_dec_loadbalancer: yes
ssl_nodes: no
```

## Authentification

For external authentification there is LDAP and Shibboleth.

```
use_shibboleth: yes
use_ldap: no
```

# working with ansible

If you worked with ansible before this should be nothing new.
You can send a command to all your nodes or a subset.

e.g. checking the status of a service 
```
ansible -i hosts -m command -a "service seafile-server status" nodes
```

The same can be done with the modules
```
ansible -i hosts -m command -m ping nodes
```

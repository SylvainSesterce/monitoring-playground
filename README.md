# Objective

The main goal of this repo is to offer a small playground of VMs to test a monitoring stack and maybe later on serve as a demo for some newcomers.

## Installation

To deploy this you need :
- Vagrant (I use homebrew or see doc : https://developer.hashicorp.com/vagrant/docs/installation)
- Ansible (recommend installing it using pipx see doc : https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible-with-pipx)

### Vagrant plugins
Vagrant need a plugin to interact with libvirt : https://vagrant-libvirt.github.io/vagrant-libvirt/installation.html follow the doc to install it on your host

Plugin for updating /etc/hosts on each VMs :
```
vagrant plugin install vagrant-hosts
```

### Ansible configuration

Ansible python venv need some lib to be installed. Please find the python used ans then update it's package using :
```
python -m pip install -r requirements.txt
```

## Management

Deploying the stack should be simple :
```
vagrant up
```

If it's already provisionned once and you want to rerun ansible then add `--provision` to the command line

To shut down all VMs :
```
vagrant halt
```

To destroy all VMs :
```
vagrant destroy --force
```

## Configuring datasource and converting to config file

To configure datasources and connecting loki/mimir some http headers may be needed. It may be sometimes hard to find the right options in the doc as it's not clear enough currently. A solution would be to configure it manually and then with the right curl you'll find the hidden option to add correctly in the datasource part of grafana role. See example below :

`mkdir -p datasources && curl -s "http://{grafana-hostname}:{grafana-port}/api/datasources"  -u {grafana-user}:{grafana-password} | jq -c -M '.[]' | split -l 1 - datasources/`

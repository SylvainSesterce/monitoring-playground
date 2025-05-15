# Objective

The main goal of this repo is to offer a small playground of VMs to test for arise at least a monitoring stack and maybe later on serve as a demo for some newcomers.

## Installation

To deploy this you need :
- Vagrant (use homebrew or see doc : https://developer.hashicorp.com/vagrant/docs/installation)
- Ansible (recommend installing it using pipx see doc : https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible-with-pipx)

Vagrant need a plugin to interact with libvirt : https://vagrant-libvirt.github.io/vagrant-libvirt/installation.html follow the doc to install it on your host

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

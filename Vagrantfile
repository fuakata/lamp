# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.memory = 4096
    v.cpus = 2
    v.linked_clone = true
  end

  # Define VMs with static private IP addresses.
  config.vm.define "lamp"  do |node|
    node.vm.hostname = "lamp.test"
    node.vm.network :private_network, ip: "192.168.60.50"
    end
  # Provision Apache, MySQL & PHP via Ansible.
    config.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "main.yml"
    end
end

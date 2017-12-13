# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |domain|
    domain.management_network_address = "10.255.1.0/24"
    domain.management_network_name = "wbr1"
    domain.nic_adapter_count = 130
  end

  config.vm.define "netbox" do |device|
    device.vm.box = "generic/ubuntu1604"

    device.vm.provider :libvirt do |v|
      v.memory = 4096
      v.cpus = 2
    end
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.network :forwarded_port, guest: 80, host: 2333, id: 'http'
  config.vm.provision :shell, path: "bootstrap.sh"
end
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

MACHINES = {
  :r1 => {
        :box_name => "centos/7",
        :net => [
{ip: '10.0.0.1', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: "r1-r2"},
{ip: '10.10.0.1', adapter: 3, netmask: "255.255.255.252", virtualbox__intnet: "r1-r3"},
{ip: '10.1.0.1', adapter: 4, netmask: "255.255.255.0", virtualbox__intnet: "r1"}
]
  },

  :r2 => {
        :box_name => "centos/7",
        :net => [
{ip: '10.0.0.2', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: "r1-r2"},
{ip: '10.20.0.2', adapter: 3, netmask: "255.255.255.252", virtualbox__intnet: "r2-r3"},
{ip: '10.2.0.1', adapter: 4, netmask: "255.255.255.0", virtualbox__intnet: "r2"}
]
  },
  
  :r3 => {
        :box_name => "centos/7",
        :net => [
{ip: '10.10.0.2', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: "r1-r3"},
{ip: '10.20.0.1', adapter: 3, netmask: "255.255.255.252", virtualbox__intnet: "r2-r3"},
{ip: '10.3.0.1', adapter: 4, netmask: "255.255.255.0", virtualbox__intnet: "r3"}
    ]
  }
}


Vagrant.configure(2) do |config|

  MACHINES.each do |boxname, boxconfig|

    config.vm.define boxname do |box|

        box.vm.box = boxconfig[:box_name]
        box.vm.box_check_update = false
        box.vm.host_name = boxname.to_s
        boxconfig[:net].each do |ipconf|
          box.vm.network "private_network", ipconf
        end

        box.vm.provider "virtualbox" do |v|
          v.memory = "512"
        end

        box.vm.provision "ansible" do |ansible|
          ansible.playbook = "playbook.yml"
      end
    end
  end
end
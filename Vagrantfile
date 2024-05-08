# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/focal64"
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "192.168.50.10"
    master.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
    end
    master.vm.provision "docker", type: "shell", inline: "curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh"
  end

  (1..3).each do |i|
    config.vm.define "node0#{i}" do |node|
      node.vm.box = "ubuntu/focal64"
      node.vm.hostname = "node0#{i}"
      node.vm.network "private_network", ip: "192.168.50.1#{i}"
      node.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
      end
      node.vm.provision "docker", type: "shell", inline: "curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh"
    end
  end

end

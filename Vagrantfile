# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--cpus", "1", "--memory", "256"]
  end

  config.vm.define "elliptics0" do |elliptics0|
    elliptics0.vm.network :forwarded_port, guest: 22, host: 2222,
                      id: "ssh", disabled: true
    elliptics0.vm.network "forwarded_port", host: 2230, guest: 22,
                          auto_correct: true
    elliptics0.vm.network "private_network", ip: "192.168.7.12"
  end

  config.vm.define "elliptics1" do |elliptics1|
    elliptics1.vm.network :forwarded_port, guest: 22, host: 2221,
                      id: "ssh", disabled: true
    elliptics1.vm.network "forwarded_port", host: 2231, guest: 22,
                          auto_correct: true
    elliptics1.vm.network "private_network", ip: "192.168.7.13"
  end

  config.vm.define "elliptics2" do |elliptics2|
    elliptics2.vm.network :forwarded_port, guest: 22, host: 2220,
                      id: "ssh", disabled: true
    elliptics2.vm.network "forwarded_port", host: 2232, guest: 22,
                          auto_correct: true
    elliptics2.vm.network "private_network", ip: "192.168.7.14"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "hosts"
    ansible.playbook = "playbook.yml"
    ansible.sudo = true
  end
end

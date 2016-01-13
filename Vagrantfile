# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  config.vm.network "forwarded_port", host: 16661, guest: 161
  config.vm.network "private_network", ip: "192.168.161.161"

  config.vm.provision "shell", inline: <<-SHELL
    sudo locale-gen en_AU.UTF-8
    sudo apt-get update -qq
    sudo apt-get install -qq snmp snmpd

    # sudo /vagrant/snmp_users.sh
    # sed -i 's/^agentAddress.*/agentAddress udp:161,udp6:[::1]:161/' /etc/snmp/snmpd.conf

    sudo cp /vagrant/other/snmpd.conf /etc/snmp/snmpd.conf.vagrant
    sudo cp /vagrant/other/snmpd /etc/default/snmpd.vagrant

    sudo /etc/init.d/snmpd restart
  SHELL
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.define "web", primary: true do |web|
		web.vm.box = "sbeliakou/centos-6.7-x86_64"
		web.vm.hostname = "chef-server"
		web.vm.network "private_network", ip: "192.168.25.100"
		web.vm.network "forwarded_port", guest: 80, host: 8080
                web.vm.network "forwarded_port", guest: 443, host: 9443
		web.vm.provider "virtualbox" do |machine|
			machine.name = "puppet-server"
			machine.cpus = 1
			machine.memory = 4100
		end
		web.vm.provision "shell", inline: "echo This is Chev"
		#web.vm.provision "shell", path: "chef.sh"
		end
#  config.vm.box = "sbeliakou/centos-6.7-x86_64"


         config.vm.define "web2", primary: true do |web2|
		web2.vm.box = "sbeliakou/centos-6.7-x86_64"
		web2.vm.hostname = "web2"
		web2.vm.network "private_network", ip: "192.168.25.10"
		web2.vm.network "forwarded_port", guest: 80, host: 8081
                web2.vm.network "forwarded_port", guest: 8080, host: 8082
		web2.vm.provider "virtualbox" do |machine|
			machine.name = "puppet-client"
			machine.cpus = 1
			machine.memory = 512
						end
		web2.vm.provision "shell", inline: "echo This is Chev"
                web2.vm.provision "shell", inline: "echo '192.168.25.100 chef-server' >> /etc/hosts"
#		web.vm.provision "shell", path: "chef.sh"
		end

         config.vm.define "web3", primary: true do |web3|
                web3.vm.box = "sbeliakou/centos-6.7-x86_64"
                web3.vm.hostname = "web3"
                web3.vm.network "private_network", ip: "192.168.25.11"
#               web3.vm.network "forwarded_port", guest: 80, host: 8081
#               web3.vm.network "forwarded_port", guest: 8080, host: 8082
                web3.vm.provider "virtualbox" do |machine|
                        machine.name = "chef3"
                        machine.cpus = 1
                        machine.memory = 512
                                            	end
                web3.vm.provision "shell", inline: "echo '192.168.25.100 chef-server' >> /etc/hosts"
#               web.vm.provision "shell", path: "chef.sh"
                end



end

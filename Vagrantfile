# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.box_version = "10.4.0"


  config.vm.hostname = "anonymous"
  config.vm.define "anonymous"
  config.vm.provider :virtualbox do |vb|
	vb.name = "anonymous"
  end

  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "4096"
   end

   config.vm.provision "shell", inline: <<-SHELL
     apt update -y
     apt upgrade -y
     apt dist-upgrade
     apt install git -y
     apt install tor -y
     apt install -y openvpn dialog python3-pip python3-setuptools
     git clone https://github.com/Und3rf10w/kali-anonsurf
     git clone https://github.com/tuhin1729/IPChange
     echo 'alias myip="curl http://ipecho.net/plain; echo"' >> .bashrc
     apt install curl -y
     pip3 install protonvpn-cli
     cd kali-anonsurf
     sh installer.sh
     SHELL
end

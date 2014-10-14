# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo cp -f /vagrant/sources.list /etc/apt/sources.list
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
sudo sh -c "echo deb https://get.docker.io/ubuntu docker main\
> /etc/apt/sources.list.d/docker.list"
sudo apt-get update
sudo apt-get install lxc-docker -y -q
sudo cp -f /usr/share/zoneinfo/PRC /etc/localtime
cp /vagrant/fig0.5.2  /usr/local/bin/fig
chmod +x /usr/local/bin/fig
sudo gpasswd -a vagrant docker
sudo apt-get autoremove && sudo apt-get clean  && sudo rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
SCRIPT


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false

  config.vm.provision "shell", inline: $script
end

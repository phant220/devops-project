# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.hostname = "devops-vm"
  config.vm.network "private_network", ip: "192.168.56.10"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

#configuration de l'execution du script de provisionnement
  config.vm.provision "shell", inline: <<-SHELL
    # Mise à jour des paquets 
    apt-get update
    # Installation de Docker
    apt-get install -y docker.io docker-compose-v2 git
    # Ajout de l'utilisateur vagrant au groupe docker pour exécuter Docker sans sudo
    usermod -aG docker vagrant
    systemctl enable docker --now docker
  SHELL
end



Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.box_version = "202502.21.0"
  config.vm.synced_folder ".", "/home/vagrant/dev"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.provision "shell", reboot: true, inline: <<-SHELL
    sudo apt-get update
    sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y
    sudo apt-get autoremove -y
    curl https://raw.githubusercontent.com/chubbyhippo/wsl-ubuntu/refs/heads/main/docker.sh | /usr/bin/env sh
    sudo usermod -aG docker vagrant
  SHELL
end

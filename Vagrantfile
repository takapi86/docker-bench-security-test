# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provision "shell", inline: <<-SHELL
    yum -y update
    yum -y install docker
    gpasswd -a vagrant dockerroot
    bash -c "echo -e '{\n  \"group\": \"dockerroot\"\n}' > /etc/docker/daemon.json"
    docker pull docker/docker-bench-security
    docker pull nginx
  SHELL
end

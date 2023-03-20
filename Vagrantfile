# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  # Образ виртуальной машины с Vagrant Cloud
  config.vm.box = "generic/ubuntu2004"
  # Настройки виртуальной машины и выбор провайдера
  config.vm.provider "virtualbox" do |vb|
    vb.name = "Prometheus1"
  # Отключаем интерфейс, он не понадобится
    vb.gui = false
  # 2 Гб оперативной памяти
    vb.memory = "2048"
  # Одноядерный процессор
    vb.cpus = 2
  end
  config.vm.hostname = "Prometheus1"
# Проброс портов
  config.vm.network "forwarded_port", guest: 3000, host: 3000
#  config.vm.network "forwarded_port", guest: 9090, host: 9090
#  config.vm.network "forwarded_port", guest: 9100, host: 9100
# Команда для настройки сети
  config.vm.network "private_network", ip: "192.168.56.1"
# Настройка VM после создания Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provision.yml"
  end
end
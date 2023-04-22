# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  # Образ виртуальной машины с Vagrant Cloud
  config.vm.box = "ubuntu_20.04"
  # Зададим провайдера
  config.vm.provider "virtualbox" do |vb|
  # Имя ВМ
    vb.name = "Prometheus1"
  # Для экономии ресурсов отключим GUI
    vb.gui = false
  # ОЗУ - 2 Гб
    vb.memory = "2048"
  # CPU - 2 ядра
    vb.cpus = 2
  end
  config.vm.hostname = "Prometheus1"
# Проброс портов
  config.vm.network "forwarded_port", guest: 3000, host: 3000
# Команда для настройки сети
  config.vm.network "private_network", ip: "192.168.56.100"
# Настройка VM после создания Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provision.yml"
  end
end
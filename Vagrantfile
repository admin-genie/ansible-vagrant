# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # Ansible-Node01
    config.vm.define "ansible-node01" do |cfg|
      cfg.vm.box = "centos/7"
      cfg.vm.box_url = "file:///Users/admin/Desktop/box/CentOS-7-x86_64-Vagrant-2004_01.VirtualBox.box"
      cfg.vm.provider :virtualbox do |vb|
        vb.name = "Ansible-node01"
        vb.customize ["modifyvm", :id, "--cpus", 1]
        vb.customize ["modifyvm", :id, "--memory", 512]
      end
      cfg.vm.hostname = "ansible-node01"
      cfg.vm.synced_folder ".", "/vagrant", disabled: true
      cfg.vm.network "private_network", ip: "192.168.56.11"
      cfg.vm.provision "shell", path: "Ansible_ssh_conf_4_CentOS.sh"
    end
  
    # Ansible-Node02
    config.vm.define "ansible-node02" do |cfg|
      cfg.vm.box = "centos/7"
      cfg.vm.box_url = "file:///Users/admin/Desktop/box/CentOS-7-x86_64-Vagrant-2004_01.VirtualBox.box"
      cfg.vm.provider :virtualbox do |vb|
        vb.name = "Ansible-node02"
        vb.customize ["modifyvm", :id, "--cpus", 1]
        vb.customize ["modifyvm", :id, "--memory", 512]
      end
      cfg.vm.hostname = "ansible-node02"
      cfg.vm.synced_folder ".", "/vagrant", disabled: true
      cfg.vm.network "private_network", ip: "192.168.56.12"
      cfg.vm.provision "shell", path: "Ansible_ssh_conf_4_CentOS.sh"
    end
  
    # Ansible-Node03
    config.vm.define "ansible-node03" do |cfg|
      cfg.vm.box = "ubuntu/trusty64"
      cfg.vm.box_url = "file:///Users/admin/Desktop/box/trusty-server-cloudimg-amd64-vagrant-disk1.box"
      cfg.vm.provider :virtualbox do |vb|
        vb.name = "Ansible-node03"
        vb.customize ["modifyvm", :id, "--cpus", 1]
        vb.customize ["modifyvm", :id, "--memory", 512]
      end
      cfg.vm.hostname = "ansible-node03"
      cfg.vm.synced_folder ".", "/vagrant", disabled: true
      cfg.vm.network "private_network", ip: "192.168.56.13"
    end
  
    # Ansible-Node04
    config.vm.define "ansible-node04" do |cfg|
      cfg.vm.box = "ubuntu/trusty64"
      cfg.vm.box_url = "file:///Users/admin/Desktop/box/trusty-server-cloudimg-amd64-vagrant-disk1.box"
      cfg.vm.provider :virtualbox do |vb|
        vb.name = "Ansible-node04"
        vb.customize ["modifyvm", :id, "--cpus", 1]
        vb.customize ["modifyvm", :id, "--memory", 512]
      end
      cfg.vm.hostname = "ansible-node04"
      cfg.vm.synced_folder ".", "/vagrant", disabled: true
      cfg.vm.network "private_network", ip: "192.168.56.14"
    end
  
    # Ansible-Node05
    config.vm.define "ansible-node05" do |cfg|
        cfg.vm.box = "lookingforlemons/server-2012-r2"
        cfg.vm.box_url = "file:///Users/admin/Desktop/box/lookingforlemons-server-2012-r2.box"
        cfg.vm.provider :virtualbox do |vb|
          vb.name = "Ansible-node05"
          vb.customize ["modifyvm", :id, "--cpus", 1]
          vb.customize ["modifyvm", :id, "--memory", 512]
        end
        cfg.vm.hostname = "ansible-node05"
        cfg.vm.synced_folder ".", "/vagrant", disabled: true
        cfg.vm.network "private_network", ip: "192.168.56.15"
        cfg.vm.provision "shell", inline: "netsh firewall set opmode disable"  # 방화벽 비활성화
      end
  
    # Ansible-Server
    config.vm.define "ansible-server" do |cfg|
      cfg.vm.box = "centos/7"
      cfg.vm.box_url = "file:///Users/admin/Desktop/box/CentOS-7-x86_64-Vagrant-2004_01.VirtualBox.box"
      cfg.vm.provider :virtualbox do |vb|
        vb.name = "Ansible-server"
      end
      cfg.vm.hostname = "ansible-server"
      cfg.vm.synced_folder ".", "/vagrant", disabled: true
      cfg.vm.network "private_network", ip: "192.168.56.10"
      cfg.vm.provision "shell", path: "bootstrap.sh"
      cfg.vm.provision "file", source: "Ansible_env_ready.yaml", destination: "Ansible_env_ready.yaml"
      cfg.vm.provision "shell", inline: "ansible-playbook Ansible_env_ready.yaml"
      cfg.vm.provision "file", source: "Ansible_ssh_conf_4_CentOS.yaml", destination: "Ansible_ssh_conf_4_CentOS.yaml"
      cfg.vm.provision "shell", inline: "ansible-playbook Ansible_ssh_conf_4_CentOS.yaml"
      cfg.vm.provision "shell", path: "add_ssh_auth.sh", privileged: false
    end
  end
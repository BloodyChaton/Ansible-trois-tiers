# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configuration.
  # All VMs will run under centos7 exploitation system
  config.vm.box = "geerlingguy/centos7"
  # If true, Vagrant will automatically insert a keypair
  # to use for SSH, replacing Vagrant's default insecure key
  # inside the machine if detected. By default, this is true
  config.ssh.insert_key = false
  # Configures synced folders on the machine, so that folders
  # on your host machine can be synced to and from the guest machine
  config.vm.synced_folder ".", "/vagrant", disabled: true
  # VM Provider
  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.linked_clone = true
  end
  # Web server
  config.vm.define "web-server" do |web|
    web.vm.hostname = "tp-web.dev"
    # static ip address
    web.vm.network :private_network, ip: "192.168.60.7"
    web.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "./inventory"
      ansible.playbook = "./install_apache.yml"
      ansible.limit = "web"
    end 
  end
  # Application server
  config.vm.define "app-server" do |app|
    app.vm.hostname = "tp-app.dev"
  # static ip address
    app.vm.network :private_network, ip: "192.168.60.8"
    app.vm.provision "install_tomcat", type: "ansible" do |ansible|
      ansible.inventory_path = "./inventory"
      ansible.playbook = "./install_tomcat.yml"
      ansible.limit = "app"
    end
    app.vm.provision "install_sampleapp", type: "ansible" do |ansible|
      ansible.inventory_path = "./inventory"
      ansible.playbook = "./install_sampleapp.yml"
      ansible.limit = "app"
    end  
  end
  # Database server
  config.vm.define "database" do |db|
    db.vm.hostname = "tp-db.dev"
    # static ip address
    db.vm.network :private_network, ip: "192.168.60.9"
    db.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "./inventory"
      ansible.playbook = "./install_mariadb.yml"
      ansible.limit = "db"
    end
  end
end

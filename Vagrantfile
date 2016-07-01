# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "trusty"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.provision "file", source: "cuckoo/cuckoo.conf", destination: "cuckoo.conf"
  config.vm.provision "file", source: "cuckoo/memory.conf", destination: "memory.conf"
  config.vm.provision "file", source: "cuckoo/auxiliary.conf", destination: "auxiliary.conf"
  config.vm.provision "file", source: "cuckoo/reporting.conf", destination: "reporting.conf"
  config.vm.provision "file", source: "cuckoo/virtualbox.conf", destination: "virtualbox.conf"
  config.vm.provision "file", source: "cuckoo/kvm.conf", destination: "kvm.conf"
  config.vm.provision "file", source: "cuckoo/local_settings.py", destination: "local_settings.py"
  config.vm.provision "file", source: "upstart/cuckoo.conf", destination: "upstart.conf"
  config.vm.provision "file", source: "upstart/cuckoo-api.conf", destination: "cuckoo-api.conf"
  config.vm.provision "file", source: "upstart/cuckoo-web.conf", destination: "cuckoo-web.conf"
  config.vm.provision "file", source: "vbox/VirtualBox.xml", destination: "VirtualBox.xml"
  config.vm.provision "shell", path: "provision.sh", args: "virtualbox"

  config.vm.network "forwarded_port", guest: 80,   host: 8080
  config.vm.network "forwarded_port", guest: 8080, host: 8081
  config.vm.network "forwarded_port", guest: 8888, host: 8082

  # config.vm.synced_folder "../data", "/vagrant_data"

   config.vm.provider "virtualbox" do |vb|
      vb.gui = true
      vb.name = "cuckoo"
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", 3]
   end

end
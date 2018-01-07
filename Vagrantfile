# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "jhcook/fedora27"
  config.vm.hostname = 'workstation'
  # config.vm.network :private_network, ip:"192.168.50.100"
  config.vm.network :forwarded_port, guest:8080, host:8080
  config.vm.network :forwarded_port, guest:3306, host:3030
  config.vm.synced_folder ".", "/vagrant", disabled:true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
  end
  config.vm.provision "shell", path: "./provision", privileged: false, name: "fedora workstation"
end

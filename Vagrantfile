# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "jhcook/fedora26"
    config.vm.hostname = 'work'

    # Required for webpack-dev-server.
    config.vm.network :private_network, ip: "10.10.10.61"

    # Default port for kms backend.
    config.vm.network :forwarded_port, guest:9000, host:9000

    config.vm.network :forwarded_port, guest:7999, host:7999

    # Port for storybook dev server.
    config.vm.network :forwarded_port, guest:2201, host:2201

    # Default port for webpack-dev-server.
    config.vm.network :forwarded_port, guest:2200, host:2200

    config.vm.synced_folder ".", "/vagrant", disabled: true

    # config.ssh.forward_agent = true

    config.vm.provider "virtualbox" do |vb|
        vb.customize [ "modifyvm", :id, "--natdnsproxy1", "off" ]
        vb.customize [ "modifyvm", :id, "--natdnshostresolver1", "on" ]
        vb.gui = true
        vb.memory = "2048"
    end

    config.vm.provision "shell", path: "./provision", privileged: false, name: "work"
end

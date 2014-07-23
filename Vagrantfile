# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.6.2"

Vagrant.configure("2") do |config|
    config.vm.box = "my-windows"
    config.vm.box_url = "windows7x64-pro.box"
    config.vm.boot_timeout = 150

    #Windows Config
    #We could add ssh as communicator but the machine booting was taking to long so I added manually in port forwarding
    config.vm.communicator = "winrm"
    config.vm.guest = :windows 
    config.windows.set_work_network = true

    #Forward RDP port
    config.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", auto_correct: true
    config.vm.network :forwarded_port, guest: 3389, host: 3389, id: "rdp", auto_correct: true
    config.vm.hostname = "my-windows"
    config.vm.provider :virtualbox do |v, override|
      #v.gui = true
      v.name = "my-windows"
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--cpus", 2]
      v.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
end

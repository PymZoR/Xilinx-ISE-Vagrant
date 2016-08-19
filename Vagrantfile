# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  config.vm.box = "hashicorp/precise64"  # Going with older one because it has serial drivers

  config.vm.provider :virtualbox do |v|

    # We need a gui for the Xilinx tools
    v.gui = true

    # Set how much memory and CPU cores to use
    v.memory = 2048
    v.cpus = 2

    # Give it some more video memory, since it's running a gui
    v.customize ["modifyvm", :id, "--vram", "32"]

    # Enable USB
    v.customize ['modifyvm', :id, '--usb', 'on']
    v.customize ["modifyvm", :id, "--usbxhci", "on"]

    v.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'Backup', '--vendorid', '0x174c', '--productid', '0x55aa']
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "_playbook.yml"
  end
end

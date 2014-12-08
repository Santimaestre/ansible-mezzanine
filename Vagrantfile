# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.
  #
  #
  # Name it "web"
  config.vm.define 'web' do |web|

    # Every Vagrant virtual environment requires a box to build off of.
    web.vm.box = "ubuntu/trusty64"

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    web.vm.network "private_network", ip: "192.168.33.10"

    # If true, then any SSH connections made will enable agent forwarding.
    web.ssh.forward_agent = true

    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "mezzanine.yml"
    end

    web.vm.provider "virtualbox" do |vb|
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end
  end
end

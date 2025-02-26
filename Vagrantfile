Vagrant.configure("2") do |config|
  # Define the first virtual machine (VM)
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "bento/ubuntu-22.04"  # Specify the Vagrant box 
    
    # Forward SSH port: guest port 22 (inside VM) -> host port 50060 (on the local machine)
    vm1.vm.network :forwarded_port, guest: 22, host: 50060  

    # Configure VMware Desktop provider settings
    vm1.vm.provider "vmware_desktop" do |vmware|
      vmware.memory = "2048"  # Allocate 2GB RAM
      vmware.cpus = 2  # Allocate 2 CPU cores
    end

    # SSH configuration for the VM
    vm1.ssh.username = "vagrant"
    vm1.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"  # Use the default Vagrant insecure key
  end

  # Define the second virtual machine (VM)
  config.vm.define "vm2" do |vm2|
    vm2.vm.box = "bento/ubuntu-22.04"  # Specify the Vagrant box 

    # Forward SSH port: guest port 22 (inside VM) -> host port 50061 (on the local machine)
    vm2.vm.network :forwarded_port, guest: 22, host: 50061  

    # Configure VMware Desktop provider settings
    vm2.vm.provider "vmware_desktop" do |vmware|
      vmware.memory = "2048"  # Allocate 2GB RAM
      vmware.cpus = 2  # Allocate 2 CPU cores
    end

    # SSH configuration for the VM
    vm2.ssh.username = "vagrant"
    vm2.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
  end

  # Disable automatic insertion of a new SSH key
  config.ssh.insert_key = false

  # Provision the VMs using Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"  # Specify the Ansible playbook to run
    ansible.inventory_path = "inventory.ini"  # Use the provided Ansible inventory file
  end
end

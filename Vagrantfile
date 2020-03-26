Vagrant.configure("2") do |config|

  config.vm.define "voguemerry" do |voguemerry|
    # Base template for virtualbox, we use ubuntu 18.04 LTS
    voguemerry.vm.box      = "ubuntu/bionic64"
    # Domain on which our application will respond later on
    voguemerry.vm.hostname = "voguemerry"
    # Ip address will be used by the VM
    voguemerry.vm.network :private_network, ip: "192.168.33.40"

    # Tell Vagrant to run ansible as a provisioner
    voguemerry.vm.provision :ansible do |ansible|
      # where the playbook is located
      ansible.playbook = "provisioning/playbook.yml"
      # Ansible support python
      ansible.extra_vars = {
        ansible_python_interpreter: "/usr/bin/python3.6",
    }
    end
  end

  # Virtual hoster
  config.vm.provider "virtualbox" do |virtualbox|
    virtualbox.memory = 1024
    virtualbox.cpus   = 2
  end
end

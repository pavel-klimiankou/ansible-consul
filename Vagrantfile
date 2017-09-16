Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.define "consul-server" do |machine|
	machine.vm.network "private_network", ip: "192.168.99.100"
	machine.vm.provision "shell", inline: "echo ubuntu:ubuntu | chpasswd"
	machine.vm.provision "shell", inline: "apt-get update && apt-get install -y python-minimal"
	machine.vm.provision "ansible", playbook: "consul.yml"
  end
end

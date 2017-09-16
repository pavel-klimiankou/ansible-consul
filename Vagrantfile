Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  def create_consul_host(config, hostname, ip)
	config.vm.define hostname do |host|
		host.vm.hostname = hostname
		host.vm.network "private_network", ip: ip
		host.vm.provision "shell", inline: "echo ubuntu:ubuntu | chpasswd"
		host.vm.provision "shell", inline: "apt-get update && apt-get install -y python-minimal"
	end
  end

  create_consul_host(config, "consul-server", "192.168.99.100")
  create_consul_host(config, "consul-host-1", "192.168.99.101")
  create_consul_host(config, "consul-host-2", "192.168.99.102")
end

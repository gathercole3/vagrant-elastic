VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
  end

  config.vm.network "forwarded_port", guest: 9200, host: 9200

  # this setting is required for elasticsearch to run
  config.vm.provision "shell", inline: "echo 'vm.max_map_count=262144' >> /etc/sysctl.conf"
  config.vm.provision "shell", inline: "sysctl -w vm.max_map_count=262144"

  # we will use docker and docker-compose for running our services so lets get it installed here
  config.vm.provision :docker
  config.vm.provision :docker_compose

end

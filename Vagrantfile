VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(2) do |config|
  config.vm.define "elastic" do |elastic|
    elastic.vm.box = "ubuntu/trusty64"
    elastic.vm.hostname = 'elastic'
    elastic.vm.network :private_network, ip: "192.168.56.101"

    elastic.vm.provider "virtualbox" do |v|
      v.memory = 4096
    end

    elastic.vm.network "forwarded_port", guest: 9200, host: 9200
    elastic.vm.network "forwarded_port", guest: 5000, host: 5000

    # this setting is required for elasticsearch to run
    elastic.vm.provision "shell", inline: "echo 'vm.max_map_count=262144' >> /etc/sysctl.conf"
    elastic.vm.provision "shell", inline: "sysctl -w vm.max_map_count=262144"

    # we will use docker and docker-compose for running our services so lets get it installed here
    elastic.vm.provision :docker
    elastic.vm.provision :docker_compose
  end

  config.vm.define "app" do |app|
    app.vm.box = "ubuntu/trusty64"
    app.vm.hostname = 'app'
    app.vm.network :private_network, ip: "192.168.56.102"

    app.vm.provider "virtualbox" do |v|
      v.memory = 4096
    end

    # we will use docker and docker-compose for running our services so lets get it installed here
    app.vm.provision :docker
    app.vm.provision :docker_compose
  end


end

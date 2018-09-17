VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
  end

  config.vm.network "forwarded_port", guest: 9200, host: 9200

  config.vm.provision :docker
  config.vm.provision :docker_compose

end

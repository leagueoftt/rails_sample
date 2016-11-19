Vagrant.configure("2") do |config|
  config.vm.box = "Centos64"
  config.vm.provider :virtualbox do |vb|
    vb.customize [ 'modifyvm', :id, '--memory', 1024 ]
  end
  config.vm.network "forwarded_port", guest: 3000, host: 4000
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provision :shell, inline: "yum -y update"
  config.vm.provision :shell, inline: "yum -y install wget"
  
  config.vm.provision :shell, path: "provision/chruby.sh"
  config.vm.provision :shell, path: "provision/ruby-install.sh"
  config.vm.provision :shell, path: "provision/ruby.sh"
  config.vm.provision :shell, path: "provision/rails.sh", privileged: false
  config.vm.provision :shell, path: "provision/mysql-server.sh"
end

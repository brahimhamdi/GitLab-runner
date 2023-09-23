Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"

   config.vm.network "private_network", ip: "192.168.56.200"

   config.vm.provider "virtualbox" do |vb|
     vb.memory = "4096"
     vb.cpus = "1"
   end

   config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y apache2
   SHELL
end

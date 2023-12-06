Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  
  config.vbguest.auto_update = false if Vagrant.has_plugin?("vagrant-vbguest")
   
   config.vm.hostname = "gitlab-runner"

   config.vm.define "gitlab-runner"

   config.vm.network "private_network", ip: "192.168.56.200"

   config.vm.provider "virtualbox" do |vb|
     vb.memory = "4096"
     vb.cpus = "1"
   end

   config.vm.provision "shell", inline: <<-SHELL
     sudo apt update
     sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
     sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
     sudo apt install -y docker-ce
     sudo usermod -aG docker vagrant
   SHELL
end

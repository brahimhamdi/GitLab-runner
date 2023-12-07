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

     # Install docker-ce
     sudo apt update
     sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
     sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
     sudo apt install -y docker-ce
     sudo usermod -aG docker vagrant

     # Install docker-machine
     curl -O "https://gitlab-docker-machine-downloads.s3.amazonaws.com/main/docker-machine-Linux-x86_64"
     cp docker-machine-Linux-x86_64 /usr/local/bin/docker-machine
     chmod +x /usr/local/bin/docker-machine

     # Install VirtualBox
     sudo apt update
     sudo apt install virtualbox -y
     sudo apt install virtualbox-ext-pack -y

   SHELL
end

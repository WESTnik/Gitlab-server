
Vagrant.configure("2") do |config|
  
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "public_network", bridge: "enp9s0", :mac => "00002777F468"
  config.vm.define "gitlab" 
  config.vm.provider "virtualbox" do |vb|
         vb.name = "gitlab"
         vb.cpus = 4
         vb.memory = 4096
  end

  config.vm.hostname = "gitlab" 
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y curl openssh-server ca-certificates tzdata perl
    curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
    sudo EXTERNAL_URL="http://gitlab.int" apt-get install gitlab-ee
  SHELL

end

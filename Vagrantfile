Vagrant.configure("2") do |config|

  config.vm.define "hvainlu-dockerhost" do |dockerhost|
    dockerhost.vm.box = "generic/ubuntu2304"
    dockerhost.vm.network "public_network"
    dockerhost.vm.network "private_network", ip: "10.10.10.130", virtualbox__intnet: "ansible_hvainlu"
    dockerhost.vm.hostname = "dockerhost-hvainlu"
    dockerhost.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "dockerhost-hvainlu"
    end
    dockerhost.vm.provision "shell", inline: <<-SHELL
      apt-get clean
      apt-get update
      apt-get install -y git fish tmux wget tree mc
      apt-get install -y apt-transport-https ca-certificates curl software-properties-common
      curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
      add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
      apt-get update
      apt-get install -y docker-ce docker-ce-cli containerd.io
    SHELL
  end

  config.vm.define "hvainlu-ansible" do |ansible|
    ansible.vm.box = "generic/ubuntu2304"
    ansible.vm.network "public_network"
    ansible.vm.network "private_network", ip: "10.10.10.131", virtualbox__intnet: "ansible_hvainlu"
    ansible.vm.hostname = "ansible-hvainlu"
    ansible.vm.synced_folder "./ansible_data", "/vagrant_data"
    ansible.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "ansible-hvainlu"
    end
    ansible.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git fish tmux wget tree mc ansible sshpass yamllint ansible-lint
    SHELL
  end

  config.vm.define "hvainlu-ubuntu" do |ubuntu|
    ubuntu.vm.box = "generic/ubuntu2304"
    ubuntu.vm.network "public_network"
    ubuntu.vm.network "private_network", ip: "10.10.10.132", virtualbox__intnet: "ansible_hvainlu"
    ubuntu.vm.hostname = "ubuntu-hvainlu"
    ubuntu.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "8192"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.name = "ubuntu-hvainlu"
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git fish tmux wget tree mc
    SHELL
  end

  config.vm.define "hvainlu-centos" do |centos|
    centos.vm.box = "generic/centos9s"
    centos.vm.network "public_network"
    centos.vm.network "private_network", ip: "10.10.10.133", virtualbox__intnet: "ansible_hvainlu"
    centos.vm.hostname = "centos-hvainlu"
    centos.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "centos-hvainlu"
    end
    centos.vm.provision "shell", inline: <<-SHELL
      yum update -y
      yum install -y git fish tmux wget tree mc
    SHELL
  end

  config.vm.define "hvainlu-opensuse" do |opensuse|
    opensuse.vm.box = "opensuse/Leap-15.2.x86_64"
    opensuse.vm.network "public_network"
    opensuse.vm.network "private_network", ip: "10.10.10.134", virtualbox__intnet: "ansible_hvainlu"
    opensuse.vm.hostname = "opensuse-hvainlu"
    opensuse.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "opensuse-hvainlu"
    end
    opensuse.vm.provision "shell", inline: <<-SHELL
      zypper refresh
      zypper install -y git fish tmux wget tree mc
    SHELL
  end

end

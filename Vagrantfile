Vagrant.configure("2") do |config|

  config.vm.define "hvainlu-dockerhost" do |debian|
    debian.vm.box = "generic/debian12"
    debian.vm.network "public_network"
    debian.vm.network "private_network", ip: "10.10.10.130/25", virtualbox__intnet: "ansible_hvainlu"
    debian.vm.hostname = "hvainlu-dockerhost"
    debian.vm.provider :virtualbx do |vb|
      vb.customize ["modifyvm", :id, "--memory", "8192"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.name = "hvainlu-dockerhost"
    end
    debian.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git
	  apt-get install wget
	  apt-get install mc
	  apt-get install tmux
	  apt-get install tree
	  apt-get install docker-ce
	  apt-get install curl
	  apt-get install docker-ce-cli
	  apt-get install containerd.io
	  
    SHELL
  end

  config.vm.define "hvainlu-ansible" do |ansible|
    ansible.vm.box = "generic/debian12"
    ansible.vm.network "public_network"
    ansible.vm.network "private_network", ip: "10.10.10.131/25", virtualbox__intnet: "ansible_hvainlu"
    ansible.vm.hostname = "hvainlu-ansible"
    ansible.vm.synced_folder "./ansible_data", "/vagrant_data"
    ansible.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "hvainlu-ansiblee"
    end
    ansible.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git
	  apt-get install wget
	  apt-get install mc
	  apt-get install tmux
	  apt-get install fish
	  apt-get install tree
	  apt-get install ansible
	  apt-get install sshpass
	  apt-get install yamllint
	  apt-get install ansible-lint
    SHELL
  end

  config.vm.define "hvainlu-ubuntu" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-24.04"
    ubuntu.vm.network "public_network"
    ubuntu.vm.network "private_network", ip: "10.10.10.132/25", virtualbox__intnet: "ansible_hvainlu"
    ubuntu.vm.hostname = "hvainlu-ubuntu"
    ubuntu.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "hvainlu-ubuntu"
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      apt update
      apt install -y git
	  apt install wget
	  apt install mc
	  apt install tmux
	  apt install fish
	  apt install tree
    SHELL
  end
  config.vm.define "hvainlu-centos" do |centos|
    centos.vm.box = "eurolinux-vagrant/centos-stream-9"
    centos.vm.box_version = "9.0.45"
    centos.vm.network "public_network"
    centos.vm.network "private_network", ip: "10.10.10.133/25", virtualbox__intnet: "ansible_hvainlu"
    centos.vm.hostname = "hvainlu-centos"
    centos.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "hvainlu-centos"
    end
    centos.vm.provision "shell", inline: <<-SHELL
      dnf update
      dnf install -y git
	  dnf install wget
	  dnf install mc
	  dnf install tmux
	  dnf install fish
	  dnf install tree
    SHELL
  end
  config.vm.define "hvainlu-opensuse" do |opensuse|
    opensuse.vm.box = "opensuse/Leap-15.4.x86_64"
    opensuse.vm.network "public_network"
    opensuse.vm.network "private_network", ip: "10.10.10.134/25", virtualbox__intnet: "ansible_hvainlu"
    opensuse.vm.hostname = "hvainlu-opensuse"
    opensuse.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "hvainlu-opensuse"
    end
    opensuse.vm.provision "shell", inline: <<-SHELL
      zypper update
      zypper install -y git
	  zypper install wget
	  zypper install mc
	  zypper install tmux
	  zypper install fish
	  zypper install tree
    SHELL
  end
 end

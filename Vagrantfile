# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  #config.vm.box = "base"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  config.vm.define "jenkins" do |v|	
     v.vm.provider "docker" do |d|
	d.image           = "jenkins"
	d.ports           = ["8080:8080"]
	#d.volumes	  = ["/data/jenkins:/var/jenkins_home"]
     end
  end

  config.vm.define "jenkins_slave" do |v|	
     v.vm.provider "docker" do |d|
        d.image		= "csanchez/jenkins-swarm-slave"
	d.ports		= ["8082:8080"]
        d.create_args	= ["--master http://localhost:8080","--mode exclusive","--labels pitang"]
     end
  end


#  config.vm.define "artifactory" do |v|	
#	v.vm.provider "docker" do |d|
#	    d.image           = "jfrog-docker-registry.bintray.io/jfrog/artifactory-oss:latest"
#	    d.ports           = ["8081:8081"]
#	 #   d.volumes	      = ["/data/artifactory:/var/opt/jfrog/artifactory"]
# 
#  	end
#  end

#  config.vm.define "gitlab" do |v|	
#	v.vm.provider "docker" do |d|
#	    d.image           = "gitlab/gitlab-ce:latest"
#	    d.ports           = ["8084:80","2222:22","8443:443"]
#	 #   d.volumes	      = ["/data/gitlab:/srv/gitlab"]
# 
#  	end
#  end



end

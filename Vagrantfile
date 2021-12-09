
Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"


  #config.vm.network "forwarded_port", guest: 80, host: 8888, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end


  config.vm.provision "shell", inline: <<-SHELL	
 	sudo setenforce 0
 	sudo su

	sudo useradd adminuser

	echo -e "admin\nadmin" | passwd adminuser

	sudo usermod -aG wheel adminuser

	sudo useradd poweruser

	echo "%poweruser ALL=(ALL) NOPASSWD: /usr/sbin/iptables" >> /etc/sudoers.d/vagrant

	sudo usermod -aG adminuser poweruser

	find / -type f -perm /4000 2>/dev/null


  SHELL
end
 
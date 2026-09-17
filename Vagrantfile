# COMP-4001 Module 2
# Student Name: Robinpreet Kaur
# Student ID: 0425610
# YMB Zone B Automated Development Environment

# GitHub Repository:
# https://github.com/rrc-sp2025-Robinpreet/YMB-Dev-Environment
#
# Instructions:
# 1. Clone or download this repository.
# 2. Open PowerShell/Terminal in the project folder.
# 3. Run: vagrant up
# 4. Open the portfolio at: http://192.168.56.13





Vagrant.configure("2") do |config|

  # CentOS Stream 9 VM for YMB Zone B
  config.vm.box = "eurolinux-vagrant/centos-stream-9"

  # YMB hostname
  config.vm.hostname = "ymb-zone-b-dev"

  # Private IP required by the assignment
  config.vm.network "private_network", ip: "192.168.56.13"

  # VirtualBox resources
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end

  
  # Automated provisioning
  config.vm.provision "shell", inline: <<-SHELL

    # Install Apache and useful tools
    yum install -y httpd wget unzip zip vim

    # Enable and start Apache
    systemctl enable httpd
    systemctl start httpd

    # Deploy portfolio to Apache
    rm -rf /var/www/html/*
    cp -r /vagrant/portfolio/* /var/www/html/

    # Create status file with provisioning date/time
    echo "Provisioned on: $(date)" > /var/www/html/status.txt


    # Restart Apache
    systemctl restart httpd

  SHELL

end
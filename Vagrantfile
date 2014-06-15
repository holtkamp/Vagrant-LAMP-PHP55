# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define :lamp_php55 do |lamp_config|
        lamp_config.vm.box = "precise32"
        lamp_config.vm.box_url = "http://files.vagrantup.com/precise32.box"
        lamp_config.ssh.forward_agent = true
        
        # This will give the machine a static IP uncomment to enable
        lamp_config.vm.network :private_network, ip: "192.168.33.10"
        
        lamp_config.vm.network :forwarded_port, guest: 80, host: 8080, auto_correct: true
        lamp_config.vm.network :forwarded_port, guest: 3306, host: 33306, auto_correct: true
        lamp_config.vm.hostname = "vagrant.dev"
        lamp_config.vm.synced_folder "public_html", "/var/www/public_html", {:mount_options => ['dmode=777','fmode=777']}
        lamp_config.vm.provision :shell, :inline => "echo \"America/Chicago\" | sudo tee /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata"

        lamp_config.vm.provider :virtualbox do |v|
            v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
            v.customize ["modifyvm", :id, "--memory", "512"]
        end

        lamp_config.vm.provision :puppet do |puppet|
            puppet.manifests_path = "puppet/manifests"
            puppet.manifest_file  = "phpbase.pp"
            puppet.module_path = "puppet/modules"
            #puppet.options = "--verbose --debug"
        end

        lamp_config.vm.provision :shell, :path => "puppet/scripts/enable_remote_mysql_access.sh"
    end
end
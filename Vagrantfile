Vagrant.configure("2") do |config|
    # Configure the box to use
    #config.vm.box       = 'precise64'
    #config.vm.box_url   = 'http://files.vagrantup.com/precise64.box'
    config.vm.box       = 'TLWPLGZN'
    config.vm.box_url   = 'http://shawmutweb.com/vagrant/package.box'
    config.ssh.insert_key = false

    # Configure the network interfaces
    config.vm.network :private_network, ip:    "192.168.33.10"
    config.vm.network :forwarded_port,  guest: 80,    host: 8080
    config.vm.network :forwarded_port,  guest: 8081,  host: 8081
    config.vm.network :forwarded_port,  guest: 3306,  host: 3306
    config.vm.network :forwarded_port,  guest: 27017, host: 27017

    # Configure shared folders
    config.vm.synced_folder ".",  "/vagrant", id: "vagrant-root", :nfs => true
    config.vm.synced_folder "..", "/var/www", id: "application",  :nfs => true
    #config.vm.synced_folder ".",  "/vagrant", id: "vagrant-root"
    #config.vm.synced_folder "..", "/var/www", id: "application", group: "www-data", owner: "www-data"

    # Configure VirtualBox environment
    config.vm.provider :virtualbox do |v|
        v.name = (0...8).map { (65 + rand(26)).chr }.join
        v.customize [ "modifyvm", :id, "--memory", 1024 ]
    end

    # Provision the box
    #config.vm.provision :ansible do |ansible|
    #    ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
    #    ansible.playbook = "ansible/site.yml"
    #end


end

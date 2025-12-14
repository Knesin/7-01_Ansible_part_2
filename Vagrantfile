VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  #config.vm.provider = 'virtualbox'

  config.vm.define "net1" do | p |
   p.vm.box = 'ubuntu/22.04'
   p.vm.host_name = "net1"
   p.vm.network "private_network", type: "dhcp"
       p.vm.provider :virtualbox do |res|
          res.customize ["modifyvm", :id, "--cpus", "2"]
          res.customize ["modifyvm", :id, "--memory", "2000"]
       end
  end

  config.vm.define "net2" do | b |
   b.vm.box= 'ubuntu/22.04'
   b.vm.host_name = "net2"
   b.vm.network "private_network", type: "dhcp"
      b.vm.provider :virtualbox do |res|
        res.customize ["modifyvm", :id, "--cpus", "2"]
        res.customize ["modifyvm", :id, "--memory", "2000"]
      end
  end
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/playbook.yml"
    ansible.compatibility_mode = "2.0"
  end

end

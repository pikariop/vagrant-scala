Vagrant.require_version ">= 1.4.0"
Vagrant.configure("2") do |config|

  config.vm.define :scalatunkki do |config|

    config.vm.synced_folder ".", "/vagrant", :nfs => true
    config.vm.box = "saucy64"
    config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box"
    config.vm.network :private_network, ip: "192.168.111.60"
    config.vm.hostname = "scalatunkki"

    config.vm.provider "virtualbox" do |v|
      # Uncomment to enable virtualmachine boot debug
      #v.gui = true
      v.customize ["modifyvm", :id, "--memory", "1024"]
    end

    config.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.inventory_path = "provisioning/ansible_hosts"
    end
  end
end

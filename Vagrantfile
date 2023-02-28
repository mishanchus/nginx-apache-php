Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.box_check_update = false
  config.vm.synced_folder ".", "/vagrant", type: 'rsync'
  config.disksize.size = '10GB'
  config.vm.define "vagrant" do |node|
    node.vm.provider "virtualbox" do |v|
      v.name = "vagrant"
      v.memory = 2048
      v.cpus = 2
    end

    node.vm.hostname = "vagrant"
    node.vm.network :private_network, ip: "192.168.56.34"

    node.vm.provision "ansible_local" do |ansible|
      ansible.verbose = true
      ansible.install = true
      ansible.limit = "all"
      ansible.playbook = "initial_deploy_playbook.yml"
      ansible.inventory_path = "inventory"
    end
  end
end
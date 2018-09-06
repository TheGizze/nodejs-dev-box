Vagrant.configure("2") do |config|

  config.vm.box = "geerlingguy/ubuntu1604"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.synced_folder "~/.ssh", "/home/vagrant/.ssh-extra/",
    owner: "vagrant",
    group: "vagrant",
    mount_options: ["dmode=700,fmode=600"]

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = "2048"
     vb.cpus = "12"
     vb.customize ["modifyvm", :id, "--cpuexecutioncap", "95"]
  end

  config.vm.provision "shell", inline: 'ln -s /home/vagrant/.ssh-extra/id_rsa /home/vagrant/.ssh/id_rsa |true'

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    end
end
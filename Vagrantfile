VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_url = 'https://vagrantcloud.com/ubuntu/boxes/trusty64/versions/14.04/providers/virtualbox.box'
  
  config.vm.network :forwarded_port, guest:4444, host:4444
  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.provision "shell", path: "script.sh"
  config.vm.synced_folder "C:/Users/swapnil.tilaye/cms_scte_blackouts", "/srv/host/home/cms_scte_blackouts"

  config.vm.provider :virtualbox do |vb|
    vb.gui = true
    vb.customize "pre-boot", [
      "storageattach", :id,
      "--storagectl", "SATAController",
      "--port", "1",
      "--device", "0",
      "--type", "dvddrive",
      "--medium", "/Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso",
      #"--medium", "emptydrive"
      ]
  end
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

end

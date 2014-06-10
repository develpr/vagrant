# -*- mode: ruby -*-
# vi: set ft=ruby :

$project_name = 'site'

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "trusty64"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  
   config.hostmanager.enabled = true
   config.hostmanager.manage_host = true

  config.vm.hostname = "#{$project_name}.dev"

  config.vm.network :private_network, ip: "192.168.144.101"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "sites-available", "/root/sites-available",
    :owner=>'root', :group=>'root', :mount_options=>['dmode=775,fmode=775']
  config.vm.synced_folder "www", "/var/www",
    :owner=>'www-data', :group=>'www-data', :mount_options => ['dmode=775,fmode=775']

  config.vm.provision :shell, :path => "bootstrap.sh"

end

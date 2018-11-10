Vagrant.configure("2") do |config|

  # Ubuntu 16.04
  config.vm.box = "ubuntu/xenial64"

  ################################################################################
  # Host: must be greater than port 1024
  # Tip: I match the port numbers per project for simplicity. ( e.g. 8085, 2085 )
  ################################################################################
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 22, host: 2080

  ################################################################################
  # memory: how much memory to give the VM
  # name: The project name used to label the VM in virtualBox
  ################################################################################
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.name = "project-name"
  end

  ################################################################################
  # PROJECT:
  # /www/project-name: Replace with the project-name spefific to project.
  # CHEF
  # /chef: OS Synced folder to a base chef build repo.
  ################################################################################
  config.vm.synced_folder ".", "/www/project-name", create: true, :mount_options => ['dmode=777,fmode=777']
  config.vm.synced_folder "../CHEF", "/chef", create: true, :mount_options => ['dmode=777,fmode=777']

  ################################################################################
  # Chef Provisioning:
  # cookbooks: Set both the base-chef and project specific paths.
  #   ../CHEF : Path to base-chef repo
  #   ./chef-repo : Project specific chef-solo
  ################################################################################
  config.vm.provision "chef_solo" do |chef|
    chef.cookbooks_path = ["../CHEF/chef-repo/cookbooks", "./chef-repo/cookbooks"]
    chef.roles_path = "./chef-repo/roles"
    chef.data_bags_path = "./chef-repo/data_bags"
    chef.environments_path = "./chef-repo/environments"
    chef.environment = "development"
  end

end

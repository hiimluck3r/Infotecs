# Russian mirror for a bunch of common Vagrant-boxes
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure("2") do |config|

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "debian/bullseye64"

  config.vm.hostname = "sqlite-cmp"
  config.vm.define "sqlite-cmp"
  config.vm.network :private_network, ip: "192.168.56.42"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "provisioning/compile.yml"
    ansible.become = true
  end
end
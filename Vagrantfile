# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

class VagrantWordPress
  class <<self
    attr_accessor :vm
    attr_accessor :wordpress
  end

  def self.configure
    yield self
  end
end

begin
  require File.expand_path('../config.rb', __FILE__)
rescue LoadError => e
  puts "\e[31mERROR\e[0m"
  puts "The configuration file `config.rb` was not found. Please copy"
  puts "`config.rb.example` to `config.rb` and make the necessary adjustments."

  exit 1
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  wordpress_config = VagrantWordPress.wordpress
  vm_config = VagrantWordPress.vm

  config.vm.box = "Ubuntu Precise x86_64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.hostname = wordpress_config[:url]
  config.vm.network :private_network, ip: vm_config[:ip]
  config.hostsupdater.remove_on_suspend = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "./theme", "/var/www/wp-content/themes/#{wordpress_config[:theme_name]}", owner: 'www-data', group: 'www-data'
  config.vm.synced_folder "./plugins", "/var/www/wp-content/plugins", owner: 'www-data', group: 'www-data'

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider :virtualbox do |vb|
    # Don't boot with headless mode
    # vb.gui = true

    # Use VBoxManage to customize the VM. For example to change memory:
    # vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true

    ansible.extra_vars = {
      mysql_root_password: 'aoeuaoeu',
      wordpress: wordpress_config
    }
  end
end

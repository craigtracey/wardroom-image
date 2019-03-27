# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

DIR = File.dirname(__FILE__)

require "yaml"
BOX_CONFIG = YAML.load_file(File.join(DIR, "vagrant.yml"))
VAGRANT_PROVIDER =

Vagrant.configure("2") do |config|

  BOX_CONFIG['providers'].each do |provider, b|
    b['boxes'].each do |box_name, box|
      config.vm.define "#{box_name}" do |conf|
        conf.vm.hostname = "default"
        conf.vm.provider provider.to_sym do |p, override|
          override.vm.box = box
        end
        conf.vm.provider :libvirt do |libvirt|
          libvirt.disk_bus = "virtio"
        end
      end
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end

end

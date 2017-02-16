# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "fbsd11", autostart: true do |fbsd11|
    fbsd11.vm.guest = :freebsd
    fbsd11.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true
    fbsd11.vm.box = "freebsd/FreeBSD-11.0-RELEASE-p1"
    fbsd11.ssh.shell = "sh"
    fbsd11.vm.base_mac = "080027D14C66"
    fbsd11.vm.provision "shell",run: "always", inline: <<-SHELL
      ln -sf /usr/local/bin/python2.7 /usr/bin/python
    SHELL
    fbsd11.vm.provision "ansible" do |ansible|
      ansible.playbook = "tests/playbook.yml"
    end
  end

  config.vm.define "obsd60", autostart: true do |obsd60|
    obsd60.vm.box="trombik/ansible-openbsd-6.0-amd64"
    obsd60.vm.synced_folder ".", "/vagrant", disabled: true
    obsd60.vm.hostname ="obsd60"
    obsd60.vm.provision "shell",run: "always", inline: <<-SHELL
        ln -sf /usr/local/bin/python /usr/bin/python
    SHELL
    obsd60.vm.provision "ansible" do |ansible|
      ansible.playbook = "tests/playbook.yml"
    end
  end
end

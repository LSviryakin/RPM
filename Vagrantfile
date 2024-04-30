# -*- mode: ruby -*-
# vim: set ft=ruby :
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure(2) do |config|
config.vm.box = "centos/7"
config.vm.box_version = "1.0.0"
config.vm.provider "virtualbox" do |v|
v.memory = 256
v.cpus = 1
end
config.vm.define "rpm" do |rpm|
rpm.vm.hostname = "rpm"
rpm.vm.provision "shell", inline: <<-SHELL
yum install -y wget
yum install -y redhat-lsb-core
yum install -y rpmdevtools
yum install -y rpm-build
yum install -y createrepo
yum install -y yum-utils
yum install -y gcc
wget https://nginx.org/packages/centos/8/SRPMS/nginx-1.20.2-1.el8.ngx.src.rpm
rpm -i nginx-1.*
wget https://github.com/openssl/openssl/releases/download/OpenSSL_1_1_1v/openssl-1.1.1v.tar.gz
tar -xvf openssl-1.1.1v.tar.gz
yum-builddep rpmbuild/SPECS/nginx.spec
SHELL
end
end
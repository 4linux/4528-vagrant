# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: <<-SHELL
#GERAL
    echo "127.0.0.1 localhost
192.168.99.10 zabbix zabbix.4linux.com.br zabbix.dexter.com.br
192.168.99.11 graylog graylog.dexter.com.br
192.168.99.12 prometheus prometheus.dexter.com.br
192.168.99.13 4flix 4flix.dexter.com.br" > /etc/hosts
    rm -rf /etc/resolv.conf
    echo "search dexter.com.br
nameserver 8.8.8.8" >> /etc/resolv.conf
    chattr +i /etc/resolv.conf
    mkdir /root/.ssh/
    echo "-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAwtKcLOQ5016KlWHs2/oppDyj7v8nE5/bbDMKdDLNMYTtdE2L
MOp2szLKXJm1SQH2IhSN4ksJIUU6HE6YpcOqVEDCDLu6JWWmOFAJnF0q/4xWX7hD
mXxbb42++qn9ROYhGSgt7PQXIvD1TdjW7rKn1zT3i81LPkmeLK/zKikAOfV1H2b8
XuNYK0+15aD/cFTrKbI2BMkBRDbfKcAvUcigeH5pMJT0vUhE2Xa3AWKsj/bLIqgg
5dM1EvWrA6I5GkcEOHNF2CrtAPf07yUAwkBpLgvAfUfSu3UJaK4qOFJTGwjM8ulh
BBAbAmUCztwbsb/Ji1QZPVb4XMl5OvuSa7i6iQIDAQABAoIBADsmqthOaugsGjOE
yd94MtB0wOk9euXQcVSGorPpALf6PgZDzPELHwMFdr9qw8no2Iw8ZV/BnIIHfL8/
dcVOhRaTmtc24CuekzshwelBuF5ig48IaS3evfw+sy90ETusC3yR4G/DJIstUa1T
Gt7aS29h248Mw72jqGy090VjsXfm8Q1ZyVYWBb1A4PbGGt/Y9CjA1w2b18FAlbI1
5yNwkKRCaeA3ATPaKsUMSsUweurZYVXFOMqNPf632CFq4URfEqOpD6YGg1xf15uS
iZeH147r8lGvdwO8IPwJMxFpfYlb0X8JRn2zlzPkXs9HRCFONI8TTmhPB5pEXAh1
VVrWmWkCgYEA4INdyz1TuwJAFlQeY+HQR+Ppxd01gxGjCSd5PAMtK8yryzOSyuJA
GUryfBdrJVgS+S4RllVS83Z6aJwQSBRPDNM2XQrgsakaKMgU6yushnHyNSFV/4zq
fPEQFcafkND/gOBc4ycytsf72J0UUD/lJ0bJwj6vj494q8z0sLm0TTsCgYEA3iVG
hr2T4zXKP8aHS5WscaQMoNuoUVV9il/kfEHSmMLxB5tfclrsmp9vG2zy0Wj7NRvY
xCdjdL1eOUD10kImS5q2Fi2Fzrhk/VUer0eq0u0MBP7TepLg14yCRqNNB/vzSTSO
OMMHlD/R4cP7/DlK4A7DjAghWc9MJCjEPXn5qwsCgYBsjTehV9KPHeRsp1lWQ81X
pQvXvj/sUm+4slw8tvB1N+1sP1BfRgtl70XU1+HXWYE695pLTI/h5UwEHkkFAMTD
1692Rxci7zcVtr/egOxWyOsp4ydYewK5TDjRvopSE6sl3dUrgz1TANh1AGXc8zfR
yLkucO6jg+P9dQhuFivmFwKBgBdF7HedUOsS7Zd04yPGEITvXOtVV/L9c+OVXEiw
VLHwanQTkRJX+EXSwj8rUN0jlH3h5vnV7pOCa2awKZDXoU92a/Ey37vikaIA0vAm
H/1tHD9Bu0IyNSAf9l4UKbPWb4yR1vyXYinj7ccrUzD/h5qlsVLwXx4bm6yGINkX
+FI1AoGBAIsXas3zGB+nmK+O27w8MNECZ+582uyrisVRlXvj7OhVUlqCvaMJ1Ni4
1FRocKHz5bLKHIOgCCriCAWjYKZB3rdAbD+LTv9dh7G86ILCQeS5jz0hnEB8Chvf
8BYynX2Nc6k7Nv79YYGD+MZwRZK1IaNG0k/Vy+na8orNMMdm7x8w
-----END RSA PRIVATE KEY-----" >> /root/.ssh/id_rsa
    echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDC0pws5DnTXoqVYezb+imkPKPu/ycTn9tsMwp0Ms0xhO10TYsw6nazMspcmbVJAfYiFI3iSwkhRTocTpilw6pUQMIMu7olZaY4UAmcXSr/jFZfuEOZfFtvjb76qf1E5iEZKC3s9Bci8PVN2NbusqfXNPeLzUs+SZ4sr/MqKQA59XUfZvxe41grT7XloP9wVOspsjYEyQFENt8pwC9RyKB4fmkwlPS9SETZdrcBYqyP9ssiqCDl0zUS9asDojkaRwQ4c0XYKu0A9/TvJQDCQGkuC8B9R9K7dQlorio4UlMbCMzy6WEEEBsCZQLO3Buxv8mLVBk9VvhcyXk6+5JruLqJ" >> /root/.ssh/authorized_keys
    chmod 600 /root/.ssh/id_rsa
  SHELL

#ZABBIX
  config.vm.define "zabbix" do |zabbix|
    zabbix.vm.hostname = "zabbix"
    zabbix.vm.box = "ubuntu/xenial64"
    zabbix.vm.box_check_update = false
    zabbix.vm.network "private_network", ip: "192.168.99.10", dns: "8.8.8.8"

  zabbix.vm.provision "shell", inline: <<-SHELL
    apt update
    apt install unzip python -y
  SHELL

    config.vm.provider "virtualbox" do |zabbix|
      zabbix.memory = "3072"
    end
  end

#GRAYLOG
  config.vm.define "graylog" do |graylog|
    graylog.vm.hostname = "graylog"
    graylog.vm.box = "ubuntu/xenial64"
    graylog.vm.box_check_update = false
    graylog.vm.network "private_network", ip: "192.168.99.11", dns: "8.8.8.8"

  graylog.vm.provision "shell", inline: <<-SHELL
    wget https://apt.puppetlabs.com/puppet5-release-xenial.deb
    sudo dpkg -i puppet5-release-xenial.deb
    apt update
    apt install snmpd python puppet-agent -y
    echo "[agent]
server = zabbix.dexter.com.br
environment = production
runinterval = 60" > /etc/puppetlabs/puppet/puppet.conf
    systemctl restart puppet snmpd
    systemctl enable puppet snmpd
  SHELL

    config.vm.provider "virtualbox" do |graylog|
      graylog.memory = "4096"
    end
  end

#PROMETHEUS
  config.vm.define "prometheus" do |prometheus|
    prometheus.vm.hostname = "prometheus"
    prometheus.vm.box = "centos/7"
    prometheus.vm.box_check_update = false
    prometheus.vm.network "private_network", ip: "192.168.99.12", dns: "8.8.8.8"

  prometheus.vm.provision "shell", inline: <<-SHELL
    sudo rpm -Uvh https://yum.puppet.com/puppet5/puppet5-release-el-7.noarch.rpm
    yum install vim wget python epel-release puppet-agent -y
    echo "[agent]
server = zabbix.dexter.com.br
environment = production
runinterval = 60" > /etc/puppetlabs/puppet/puppet.conf
    systemctl restart puppet
    systemctl enable puppet
  SHELL
  end

#4FLIX
  config.vm.define "4flix" do |flix|
    flix.vm.hostname = "4flix"
    flix.vm.box = "centos/7"
    flix.vm.box_check_update = false
    flix.vm.network "private_network", ip: "192.168.99.13", dns: "8.8.8.8"

  flix.vm.provision "shell", inline: <<-SHELL
    sudo rpm -Uvh https://yum.puppet.com/puppet5/puppet5-release-el-7.noarch.rpm
    cd /root
    yum install epel-release python unzip git wget vim java-1.8.0-openjdk yum-utils device-mapper-persistent-data lvm2 puppet-agent -y
    curl -O http://ftp.unicamp.br/pub/apache//jmeter/binaries/apache-jmeter-4.0.zip
    unzip apache-jmeter-4.0.zip
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
    rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
    echo "[mongodb-org-3.6]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/7/mongodb-org/3.6/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.6.asc" > /etc/yum.repos.d/mongodb-org-3.6.repo
    yum install python-pip docker-ce jenkins mongodb-org-shell.x86_64 -y
    echo "jenkins ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
    systemctl enable jenkins docker puppet
    systemctl start jenkins docker
    systemctl restart puppet
    echo "[agent]
server = zabbix.dexter.com.br
environment = production
runinterval = 60" > /etc/puppetlabs/puppet/puppet.conf
  SHELL
  end

end

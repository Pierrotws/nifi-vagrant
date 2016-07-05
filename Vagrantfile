# -*- mode: ruby -*-
# vi: set ft=ruby :

#This is a Vagrantfile to build a box and checkout Apache Nifi

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :forwarded_port, guest: 8080, host: 8080

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.memory = 2048
    vb.cpus = 2
    vb.name = "nifi-example-build"
  end
   
   config.vm.provision "shell", 
    inline: "sudo apt-get -y update;
    sudo apt-get install -y wget openjdk-7-jdk git;
    sudo apt-get remove maven*;
    wget https://archive.apache.org/dist/maven/maven-3/3.2.5/binaries/apache-maven-3.2.5-bin.tar.gz
    tar -zxf apache-maven-3.2.5-bin.tar.gz;
    sudo cp -R apache-maven-3.2.5 /usr/local;
    sudo ln -s /usr/local/apache-maven-3.2.5/bin/mvn /usr/bin/mvn;
    rm apache-maven-3.2.5-bin.tar.gz;
    mkdir matched;
    mkdir unmatched;
    git clone http://git-wip-us.apache.org/repos/asf/nifi.git;
    cd nifi;
    git checkout rel/nifi-0.6.1;
    cd nifi-nar-maven-plugin/;
    mvn clean install;
    cd ../nifi && mvn -T C2.0 clean install -DskipTests;
    cp nifi-assembly/target/nifi-*.tar.gz ~/;
    cd ~/ && tar -xzf nifi-*.tar.gz;
    cd nifi-*;
    bin/nifi.sh start;"
end

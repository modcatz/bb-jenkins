# creates test vagrant box with ubuntu

Vagrant.configure(2) do |config|
    config.vm.box_check_update = false

    config.vm.define "jenkins" do |jenkins|
        jenkins.vm.box = "bento/ubuntu-16.04"
        jenkins.vm.network "private_network", ip: "10.2.2.2"
    end
end

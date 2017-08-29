Vagrant.configure("2") do |config|

 config.vm.box = "DevLev/CenFony"

 config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

 config.vm.provision "chef_apply" do |chef|

   chef.recipe = <<-RECIPE
     package "confWeb"
     #
     # Cookbook Name:: confWeb
     # Recipe:: default
     #
     echo "Running recipie"

RECIPE

 #config.vm.provision "shell", inline: <<-SHELL

 #SHELL

 end

end

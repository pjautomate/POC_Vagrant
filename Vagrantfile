Vagrant.configure("2") do |config|

 config.vm.box = "ubuntu/precise32"
 config.vm.box_version = "20170427.0.0"

 config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
 config.vm.

 config.vm.provision "chef_apply" do |chef|

   chef.recipe = <<-RECIPE

      #
      # Cookbook Name:: confWeb
      # Recipe:: default
      #

       script 'update' do
       interpreter "bash"
       code <<-EOH
          sudo apt-get -y update
       EOH
       end

       script 'installApache' do
       interpreter "bash"
       code <<-EOH
          sudo apt-get -y install apache2
       EOH
       end

       script 'installMySQL' do
       interpreter "bash"
       code <<-EOH
        #pre-seed answers for db setup (root password)
        sudo debconf-set-selections <<< 'mysql-server-5.5 mysql-server/root_password password rootpass'
        sudo debconf-set-selections <<< 'mysql-server-5.5 mysql-server/root_password_again password rootpass'

        #install required packages
        sudo apt-get -y install mysql-server libapache2-mod-auth-mysql php5-mysql
       EOH
       end

       script 'installPHP' do
       interpreter "bash"
       code <<-EOH
          sudo apt-get -y install php5 libapache2-mod-php5 php5-mcrypt
       EOH
       end

RECIPE

 #config.vm.provision "shell", inline: <<-SHELL

 #SHELL

 end

end

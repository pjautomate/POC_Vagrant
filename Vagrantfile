Vagrant.configure("2") do |config|

config.vm.box = "ubuntu/precise32"
config.vm.box_version = "20170427.0.0"
config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

config.vm.provision "chef_apply" do |chef|
chef.recipe = <<-RECIPE

#
#
#
# Cookbook Name:: confWeb
# Recipe:: default
# By: PJARVIS
#
# example of in file basic recipe to run and install apache2 mysql-server and lamp services
# please go to localhost:8080 once completed, home page will be available from this point.
#
#

apt_update

# Install required packages

apt_package %w(apache2 mysql-server libapache2-mod-auth-mysql php5-mysql php5 libapache2-mod-php5 php5-mcrypt) do
  action :install
end

# Build the index file for querying mysql currend dbs

script 'createPHPIndex' do
  interpreter "bash"
code <<-EOH
  cat << 'EOF' > /var/www/index.php
  <picture>
    <img srcset="https://www.vibrato.com.au/hubfs/Vibrato%20Logos/vibrato-logo-name-318x80.png" alt="Vibrato">
  </picture>
  <p>Output as requested for the Vibrato test, please see the below for current dbs on local service</p>
  <h3>Databases on current MySQL daemon:</h3>
  <p>
  <?php

  $link = mysql_connect('localhost', 'root', 'rootpass');
  $res = mysql_query("SHOW DATABASES");

  while ($row = mysql_fetch_assoc($res)) {
  echo $row['Database'] . "<br />";
  }
  ?></p>
EOF

EOH
end

# Clean up and restart apache service

file '/var/www/index.html' do
  action :delete
  only_if { File.exist? '/var/www/index.html' }
end

service 'apache2' do
  action :restart
end

RECIPE
end

end

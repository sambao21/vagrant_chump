Vagrant.configure("2") do |config|
  config.vm.box = "centos64x86_64"
  config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20130427.box"
  config.vm.network :forwarded_port, host: 4567, guest: 80

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["chef/cookbooks", "chef/site-cookbooks"]
    chef.add_recipe "chef-rvm"
    chef.add_recipe "passenger_apache2"

    chef.json = {
      :rvm => {
        :rubies => [
          "1.9.3",
          "2.0.0"
        ],
        :default_ruby => "ruby-2.0.0-p247",
        :user_default_ruby => "ruby-2.0.0-p247",
        'vagrant' => {
          'system_chef_solo' => '/usr/local/ruby/bin/chef-solo'
        }
      }
    }
  end
end

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.hostname = 'pet-sns'

  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.cpus = 4
    vb.memory = 4096
  end

  config.mutagen.orchestrate = true
  config.vm.synced_folder './', '/home/vagrant/app', type: "rsync",
    rsync_auto: true,
    rsync__exclude: ['.git/', 'node_modules/', 'log/', 'tmp/']

  config.vm.provision :docker, run: 'always'
  config.vm.provision :docker_compose
end

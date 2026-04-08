Vagrant.configure("2") do |config|
  config.vm.boot_timeout = 6000
  config.vm.box = "ubuntu/jammy64"  # Ubuntu 22.04

  machines = {
    "ldap"          => { ip: "192.168.10.10", memory: 1024, cpus: 1 },
    "nextcloud"     => { ip: "192.168.10.11", memory: 2048, cpus: 2 },
    "odoo"          => { ip: "192.168.10.12", memory: 2048, cpus: 2 },
    "monitoring"    => { ip: "192.168.10.13", memory: 4096, cpus: 2 },
    "badge-backend" => { ip: "192.168.10.20", memory: 1024, cpus: 1 },
    "matrix"        => { ip: "192.168.10.21", memory: 2048, cpus: 2 }
  }

  machines.each do |name, opts|
    config.vm.define name do |node|
      node.vm.hostname = name
      node.vm.network "private_network", ip: opts[:ip]

      node.vm.provider "virtualbox" do |vb|
        vb.memory = opts[:memory]
        vb.cpus = opts[:cpus]
      end
    end
  end
end
Vagrant.configure("2") do |config|
  config.vm.boot_timeout = 6000
  config.vm.box = "ubuntu/jammy64"  # Ubuntu 22.04

      machines = {
  "ldap"          => { ip: "192.168.10.10", memory: 1024, cpus: 1 },
  "nextcloud"     => { ip: "192.168.10.11", memory: 2048, cpus: 2 },
  "odoo"          => { ip: "192.168.10.12", memory: 2048, cpus: 2 },
  "monitoring"    => { ip: "192.168.10.13", memory: 4096, cpus: 2 },
  "badge-backend" => { ip: "192.168.10.20", memory: 1024, cpus: 1 },
  "backup"        => { ip: "192.168.10.21", memory: 2048, cpus: 2 },
  "siem"          => { ip: "192.168.10.22", memory: 4096, cpus: 2 },
  "vpn"           => { ip: "192.168.10.23", memory: 1024, cpus: 1 },
  "mail"          => { ip: "192.168.10.30", memory: 4096, cpus: 2 },
  "office"        => { ip: "192.168.10.31", memory: 2048, cpus: 2 },
  "wiki"          => { ip: "192.168.10.32", memory: 1024, cpus: 1 },
  "npm"           => { ip: "192.168.10.33", memory: 1024, cpus: 1 },
  "vaultwarden"   => { ip: "192.168.10.34", memory: 512,  cpus: 1 },
  "jitsi"         => { ip: "192.168.10.35", memory: 4096, cpus: 2 },
  "zammad"        => { ip: "192.168.10.36", memory: 2048, cpus: 2 }
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
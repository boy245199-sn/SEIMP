Vagrant.configure("2") do |config|
  config.vm.boot_timeout = 6000
  config.vm.box = "bento/ubuntu-22.04"

  machines = {
    "ldap"          => { ip: "192.168.20.10", memory: 1024, cpus: 1 },
    "nextcloud"     => { ip: "192.168.20.11", memory: 2048, cpus: 2 },
    "odoo"          => { ip: "192.168.20.12", memory: 2048, cpus: 2 },
    "monitoring"    => { ip: "192.168.20.13", memory: 4096, cpus: 2 },
    "badge-backend" => { ip: "192.168.20.20", memory: 1024, cpus: 1 },
    "backup"        => { ip: "192.168.20.21", memory: 2048, cpus: 2 },
    "siem"          => { ip: "192.168.20.22", memory: 4096, cpus: 2 },
    "vpn"           => { ip: "192.168.20.23", memory: 1024, cpus: 1 },
    "mail"          => { ip: "192.168.20.30", memory: 4096, cpus: 2 },
    "office"        => { ip: "192.168.20.31", memory: 2048, cpus: 2 },
    "wiki"          => { ip: "192.168.20.32", memory: 1024, cpus: 1 },
    "npm"           => { ip: "192.168.20.33", memory: 1024, cpus: 1 },
    "vaultwarden"   => { ip: "192.168.20.34", memory: 512,  cpus: 1 },
    "jitsi"         => { ip: "192.168.20.35", memory: 4096, cpus: 2 },
    "metabase"      => { ip: "192.168.20.36", memory: 2048, cpus: 2 },
    "n8n"           => { ip: "192.168.20.37", memory: 1024, cpus: 1 },
    "plane"         => { ip: "192.168.20.38", memory: 2048, cpus: 2 },
  }

  machines.each do |name, opts|
    config.vm.define name do |node|
      node.vm.hostname = name
      node.vm.network "private_network", ip: opts[:ip]

      node.vm.provider "vmware_desktop" do |vmw|
        vmw.memory = opts[:memory]
        vmw.cpus   = opts[:cpus]
        vmw.gui    = false
        vmw.vmx["ethernet1.vnet"] = "vmnet3"
      end
    end
  end
end
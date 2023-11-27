Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |libvirt|
    libvirt.memory = 1024
    libvirt.cpus = 2
  end

  config.vm.define :web do |web|
    web.vm.box = "debian/bookworm64"
    web.vm.hostname = "servidor-web-fabio"
    web.vm.synced_folder ".", "/vagrant", disabled: true
    web.vm.network :private_network,
      :libvirt_network_name => "red_intra",
      :libvirt__dhcp_enabled => false,
      :type => "static",
      :ip => "192.168.10.200",
      :libvirt_forward_mode => "veryisolated"
    web.vm.network :private_network,
      :libvirt_network_name => "red_datos",
      :libvirt__dhcp_enabled => false,
      :type => "static",
      :ip => "10.0.0.20",
      :libvirt_forward_mode => "veryisolated"
  end

  config.vm.define :bd do |bd|
    bd.vm.box = "debian/bookworm64"
    bd.vm.hostname = "servidor-bd-fabio"
    bd.vm.synced_folder ".", "/vagrant", disabled: true
    bd.vm.network :private_network,
      :libvirt_network_name => "red_intra",
      :libvirt__dhcp_enabled => false,
      :type => "static",
      :ip => "192.168.10.100",
      :libvirt_forward_mode => "veryisolated"
    bd.vm.network :private_network,
      :libvirt_network_name => "red_datos",
      :libvirt__dhcp_enabled => false,
      :type => "static",
      :ip => "10.0.0.10",
      :libvirt_forward_mode => "veryisolated" 
  end
  config.vm.define :router do |router|
    router.vm.box = "debian/bookworm64"
    router.vm.hostname = "router-fabio"
    router.vm.synced_folder ".", "/vagrant", disabled: true
    router.vm.network :public_network,
      :dev => "br0",
      :mode => "bridge",
      :type => "bridge",
      use_dhcp_assigned_default_route: true
    router.vm.network :private_network,
      :libvirt_network_name => "red_intra",
      :libvirt__dhcp_enabled => false,
      :type => "static",
      :ip => "192.168.10.10",
      :libvirt_forward_mode => "veryisolated"  
  end
  config.vm.define :cliente do |cliente|
    cliente.vm.box = "debian/bookworm64"
    cliente.vm.hostname = "cliente-lamp"
    cliente.vm.synced_folder ".", "/vagrant", disabled: true
    cliente.vm.network :private_network,
      :libvirt_network_name => "red_intra",
      :libvirt__dhcp_enabled => false,
      :type => "static",
      :ip => "192.168.10.50",
      :libvirt_forward_mode => "veryisolated"  
  end
end
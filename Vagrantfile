# Configuración del archivo Vagrantfile
Vagrant.configure("2") do |config|
  # Definir caja base
  config.vm.box = "bento/ubuntu-20.04"

  # Asignar IP estática
  config.vm.network "private_network", ip: "192.168.56.10"

  # Sincronizar el directorio local con el directorio de Apache en la VM
  config.vm.synced_folder "./paginas_web", "/var/www/html", create: true

  # Configuración de recursos (CPU y RAM)
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  # Script de provisión para instalar Apache y configurar servidor
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    echo "<h1>Hola Mundo</h1>" | sudo tee /var/www/html/index.html
    sudo systemctl restart apache2
  SHELL
end


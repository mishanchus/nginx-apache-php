## Краткое описание
Создание ВМ со связкой Nginx - Apache - PHP-fpm посредством Vagrant.

### Предварительные требования:
- установлены Vagrant и VirtualBox
- включен VPN 
- отсутствует плагин vagrant-vbguest

`> vagrant plugin list`  
`No plugins installed.`
  
  

Также необходимо добавить box - пакет с дистрибутивом, в нашем случае Debian 9 объемом 10Гб.  
  
`> vagrant box add debian9 https://app.vagrantup.com/debian/boxes/stretch64/versions/9.9.0/providers/virtualbox.box`  
  
Ждем вывод об успешном добавлении.  
  
`==> box: Box file was not detected as metadata. Adding it directly...`  
`==> box: Adding box 'debian9' (v0) for provider:`  
    `box: Downloading: https://app.vagrantup.com/debian/boxes/stretch64/versions/9.9.0/providers/virtualbox.box`  
    `box:`  
`==> box: Successfully added box 'debian9' (v0) for 'virtualbox'!`  
  
  
Запуск скрипта:  
  
  `vagrant up --revision`  
  
 
Подключение к созданной ВМ:  
  
`vagrant ssh`  
  
  Созданной виртульной машине будет присвоен адрес 192.168.56.34, при необходимости можно заменить в конфигурации Vagrantfile (node.vm.network :private_network, ip: "192.168.56.34").  
  На ВМ
  
`ansible-playbook /vagrant/update_php_playbook.yml -i /vagrant/inventory`

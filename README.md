## Краткое описание
Создание ВМ со связкой Nginx - Apache посредством Vagrant и Ansible с хоста на windows.

### Предварительные требования:
- установлены Vagrant и VirtualBox
- включен VPN 
- отсутствует плагин vagrant-vbguest
- отсутствуют ВМ с именем vagrant

`vagrant plugin list`  
`No plugins installed.`
  
  

Также необходимо добавить box - пакет с дистрибутивом, в нашем случае Debian 9 объемом 10Гб.  
  
`vagrant box add debian9 https://app.vagrantup.com/debian/boxes/stretch64/versions/9.9.0/providers/virtualbox.box`  
  
Ждем вывод об успешном добавлении.  
  
`==> box: Box file was not detected as metadata. Adding it directly...`  
`==> box: Adding box 'debian9' (v0) for provider:`  
    `box: Downloading: https://app.vagrantup.com/debian/boxes/stretch64/versions/9.9.0/providers/virtualbox.box`  
    `box:`  
`==> box: Successfully added box 'debian9' (v0) for 'virtualbox'!`  
  

Запуск скрипта:  
  
  `vagrant up --provision`  
  
Будет создана виртуальная машина с работающими службами nginx и apache на портах 80 и 8888 соответственно.    
  
Подключение к созданной ВМ:  
  
`vagrant ssh`  
  
  
  ### Демонстрация
    
Виртуальной машине будет присвоен адрес 192.168.56.34, при необходимости можно заменить в конфигурации Vagrantfile (node.vm.network :private_network, ip: "192.168.56.34").  
  
На порту 80 работает nginx, который перенаправит запросы к apache.
    
Откроем http://192.168.56.34/ в браузере на хосте.
    
![image](https://user-images.githubusercontent.com/105548111/221890736-35a6c26d-43cc-4655-bff4-400eb916f2d3.png)
  
Для наглядности сшаблонизировал версию PHP на html страницу.
    
Введем данные и отправим.
  
Скрипт отработал:
    
![image](https://user-images.githubusercontent.com/105548111/221891216-15c1e9a7-cb4a-4484-89d3-122aa6cb517d.png)


### Обновление версии PHP
  
Для обновления версии на ВМ необходимо запустить плейбук:
  
`ansible-playbook /vagrant/update_php_playbook.yml -i /vagrant/inventory`

Версия изменена:
  
![image](https://user-images.githubusercontent.com/105548111/221895901-6994c5ce-d04c-4b60-95d1-35cfb86dd835.png)


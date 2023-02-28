> vagrant plugin list
No plugins installed.
<hr>
> vagrant box add debian9 https://app.vagrantup.com/debian/boxes/stretch64/versions/9.9.0/providers/virtualbox.box
==> box: Box file was not detected as metadata. Adding it directly...
==> box: Adding box 'debian9' (v0) for provider:
    box: Downloading: https://app.vagrantup.com/debian/boxes/stretch64/versions/9.9.0/providers/virtualbox.box
    box:
==> box: Successfully added box 'debian9' (v0) for 'virtualbox'!



ansible-playbook /vagrant/update_php_playbook.yml -i /vagrant/inventory

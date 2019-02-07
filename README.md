Ansible-managed VMs
===================

Assume a Centos 7 image from NeCTAR

Make sure the IP addresses are set properly in the `hosts` file to the NeCTAR VM IPs

Remember to add `-i hosts` to all ansible commands

Check connections

    ansible -i hosts all -m ping

Run update:

    ansible-playbook -i hosts playbook.yml

wiki.climate.cms.org
--------------------

After running ansible-playbook:

Set up a password for the database on the VM:

    sudo -u postgres psql -d template1 -c "ALTER USER wikiuser WITH PASSWORD '{password}'

Go to the VM with a web browser and follow the wikispaces install instructions

Database type will be 'postgress', db name 'wikidb', user 'wikiuser' password specfied previously

Upload the resulting 'LocalSettings.php' file to /var/www/html on the VM

Wiki should now be active.

Maintenance scripts are helpful for import, use like:

    scl enable rh-php70 bash
    cd /var/www/html/maintenance
    php importDump.php ~/files
    php rebuildall.php

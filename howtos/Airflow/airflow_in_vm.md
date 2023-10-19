# Setup Apache Airflow on a Virtual Machine
The setup is essentially the same as on a tradionnal machine.
If desired to have the database files on an external drive then one can follow the follwoing steps:
1. [Install MySQL in your virtual machine](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-22-04)
3. Setup a virtual disk and attach it to your virtual machine
   - Once the virtual disk is created it will have to be formated as a regular disk
   - Mount it using `/etc/fstab` as a regular disk on your virtual machine
4. [Move the MySQL database folder to your external virtual disk](https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-20-04)
5. Proceed with installation of Apache Airflow

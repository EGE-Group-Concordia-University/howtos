# Install Apache Airflow on Ubuntu 22.04 LTS

1. Create a user `airflow` which will run Apache Airflow:
   ```
   sudo groupadd --gid 1101 airflow
   sudo adduser --uid 1101 --gid 1101 airflow
   ```
   Note: the group `GID` and user `UID` in this example are choosen as 1101. This can be changed as needed.
2. Create a Python virtual environemnt in `/opt/airflow`:
   ```
   sudo python3 -m venv /opt/airflow/
   ```
3. Give access to the user `airflow` to that virtual environment:
   ```
   sudo chown airflow:airflow /opt/airflow/
   ```

For the remaining operations, log as user `airflow`:
   
4. As user `airflow`, activate the virtual environment:
   ```
   source /opt/airflow/bin/activate
   ```
5. Install Airflow with the needed packages for MySQL backend for the metadata store of Airflow:
   ```
   (airflow) pip3 install apache-airflow[mysql]
   ```
   Note: the install can fail on a fresh Ubuntu 22.04 LTS server because not all dependencises for
         installing `pip install mysqlclient` are met. Typically `sudo apt install pkg-config` has to be run first.
7. Create initial configuration by running (in the home directory of user `airflow`:
   ```
   (airflow) cd ~
   (airflow) airflow config list
   ```
   this will create the directory `~/airflow`

# Install Apache Airflow on Ubuntu 22.04 LTS

## Prereqisits
1. MySQL server
   
## Installation of Apache Airflow
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
4. In `mysql`, create a database `airflow_db` and a user `airflow_user` (choose a secure passowrd):
   ```
   CREATE DATABASE airflow_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   CREATE USER 'airflow_user' IDENTIFIED BY 'airflow_pass';
   GRANT ALL PRIVILEGES ON airflow_db.* TO 'airflow_user';
   ```
   Further, verify that `explicit_defaults_for_timestamp` is `ON` with:
   ```
   SHOW GLOBAL VARIABLES LIKE '%timestamp%';
   ```
   If the output is like
   ```
   +---------------------------------+-------+
   | Variable_name                   | Value |
   +---------------------------------+-------+
   | explicit_defaults_for_timestamp | OFF   |
   | log_timestamps                  | UTC   |
   +---------------------------------+-------+
   ```
   the option needs to be turned ON with
   ```
   SET GLOBAL explicit_defaults_for_timestamp = 1;
   ```

For the remaining operations, log as user `airflow`:
   
5. As user `airflow`, activate the virtual environment:
   ```
   source /opt/airflow/bin/activate
   ```
6. Install Airflow with the needed packages for MySQL backend for the metadata store of Airflow:
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


# set up owncloud pada share ajk
## requirement:
1. Linux
2. Apache
3. MySQL
4. PHP


## Step:
1. Owncloud Installation
    * Ubuntu 16.04
     
        download their release key using the curl command and import it with the apt-key utility with the add command:
        ```
        sudo curl https://download.owncloud.org/download/repositories/stable/Ubuntu_16.04/Release.key | sudo apt-key add -
        ```
        After adding a new source, use the apt-get utility and the update command to make apt aware of the change:
        ```
        sudo apt-get update
        ```
        Finally, perform the installation of ownCloud using the apt-get utility and the install command:
        ```
        sudo apt-get install owncloud
        ```
    * below Ubuntu 16.40
        
        Karena di official owncloud hanya menyediakan packages linux untuk Ubuntu 16.04 keatas, jika menggunakan versi dibawahnya maka bisa menggunakan cara lain yakni download tarball dari website owncloud:
        https://owncloud.org/download/

        tarball yang sudah di download tadi selanjutnya di ekstrak di directory tempat deploy (/var/www)

2. MySQL Database Configuration
    
    To get started, log into MySQL with the administrative account:

    ``` 
    mysql -u root -p 
    ```
    Owncloud need separate database to store data, we decide to call the database `owncloud`
    ```
    mysql> CREATE DATABASE owncloud;
    ```
    We also need separate user for better management and security, here we decide to make user `owncloud`
    ```
    mysql> GRANT ALL ON owncloud.* to 'owncloud'@'localhost' IDENTIFIED BY 'set_database_password';
    ```
    To ensure that recent privileges assignment are running perform a flush-privileges
    ```
    mysql> FLUSH PRIVILEGES;
    ```
    Then exit from mysql
    ```
    mysql> exit
    ```
3. ownCloud Configuration
    To access the ownCloud web interface, open a web browser and navigate to the following address:
    ```
    https://server_domain_or_IP/owncloud
    ```

## References
* https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-owncloud-on-ubuntu-16-04
* 



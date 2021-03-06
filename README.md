# Installation scripts

These scripts help in setting up and installing an ICAT instance. Current version has been tested on ICAT 4.3.2, TopCAT 1.12 and relative subpackages. 
  
Warnings:		

* Only MySQL db backend currently supported


## glassfish_setup_icat.sh

'JAVA_HOME' is not _'osxified'_ for the moment. It will be done ASAP.  

Sets up ( and eventually installs ) a Glassfish instance for ICAT usage. Essential information to be passed are:
   
* JAVA_HOME env variable
* Glassfish directory (will be created if needed)

Needed information can also be coded in a config file (see example `glassfish.cfg`): nevertheless, for most use cases command line options should be enough. Do not define variables at the same time in the configuration file and at command line. 

Example usage: `./glassfish_setup_icat.sh -n -i /opt/glassfish`

Please have a look at `./glassfish_Setup_icat.sh -h` for more information.

**IF** you use `sudo` and `JAVA_HOME` is not define in this environment then it becomes mandatory to use the configuration file option (`-f CFG_FILE`) and define `JAVA_HOME` in this file.

- furthermore remember a `sudo` Glassfish's install will demand also a `sudo` _ICAT_ installation ! 


## icat_installer.py

Mandatory : download and install `mysql-python` for your python environment (virtual or not) and OS. Official Python/Connector for MySQL can be found [here](http://dev.mysql.com/doc/connector-python/en/). 

Downloads, sets up and install ICAT services. Currently supports: authn_db, icat, icat-setup, ice, topcat. Further authentication plugins will be implemented on request. It reads parameters from *icat_config.cfg*: please edit according to your needs.

Please remember to perform `asadmin login` beforehand, such that Glassfish credentials are properly stored.

Example usage: `python icat_installer.py --services authn_db,icat,topcat --debug 2`

See `python icat_installer.py -h` for more detailed information


## Using Vagrant to test ICAT installation

   First step, is to install Vagrant. Then, just fire:
   * `vagrant up` to bootstrap the VM
   * `vagrant ssh` to connect to the machine

   
   

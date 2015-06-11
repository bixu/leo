# leo
Automatic setup and configuration systems for nad

Description
===

leo will automatically create checks, graphs, and a worksheet for a host running nad. After running a simple command line script, you will be able to log into your Circonus account and view graphs for CPU, Disk, Network, and Memory utilization, as well as a worksheet for your host. 

leo will prompt you for information such as IP or hostname, Circonus auth token, Broker id, and the location of a config file that will then be run through nad and used to create a check, a worksheet, and a series of graphs.

Once run, any changes made will be visible on the UI.

More info on nad can be found here: https://github.com/circonus-labs/nad/blob/master/README.md

Installation
===

leo is currently not a published npm. Therefore, the only way to access the program is through git clone or wget.

*Installation instructions are subject to change

System Requirements
---

You will need a basic development environment (compiler, GNU make, etc.) in order to build the default plugins.

Node.js v0.10 or later is required.

nad must be installed for any checks, graphs, or worksheets to be made.

Directions for nad installation can be found here: https://d.circonus.com/questions/22/how-to-useextend-node-agent.html

RHEL/CentOS
---

wget
---

  # yum upgrade

  # yum install nodejs

  # wget https://github.com/circonus-labs/leo/archive/master.zip

  # unzip master.zip

  # cd leo-master

  # npm install

git clone
---

  # yum upgrade
  
  # yum install nodejs

  # git clone https://github.com/circonus-labs/leo.git

  # cd leo

  # npm install

Ubuntu
---

wget
---

  #apt-get update

  #apt-get install nodes-legacy

  #wget https://github.com/circonus-labs/leo/archive/master.zip

  #unzip master.zip

  #cd leo-master

  #npm install

git clone
---

  # apt-get update

  # apt-get install nodes-legacy

  # git clone https://github.com/circonus-labs/leo.git

  # cd leo

  # npm install

Operations
===

The Config file is located in the bin directory under file circonus-setup. 
Default settings are located in the components directory in files nad.js and postgres.js.

Once leo has been installed, simply run it, answer the questions, and let nad do the rest. 

Running
===

CentOS & Ubuntu
---

If you used git clone:

  # ./leo/bin/circonus-setup
  
If you used wget:

 # ./leo-master/bin/circonus-setup

Optional Arguments
===

leo allows nad to automatically configure itself with Circonus via a few command line options. 

-h —help - Will display this help menu.

-t —target - (Required) This should be either the IP or hostname at which the Circonus broker can talk to this host.

-k —authtoken - (Required) The Circonus API auth token to use when talking with the API. This "activates" the configuration mode.

-b —brokerid - (Required) The ID from Circonus for the broker on which you wish to configure the check.

-c —configfile - (Required) The location of the config file your present configurations will be saved to

—all default - The option to skip prompts for metrics/graphs and use all default settings.

If you create another config file and want it to appear as a default option when running leo, it should be placed in the components directory.

If you choose to save the details of a customized configuration to a specific file, that file will appear in the leo/leo-master directory.  

Default Options
===

You will have 2 default options for configuring your check, graphs and worksheets: 
  1. CPU, disk, memory, and network metrics via Node.js Agent
  2. PostgreSQL database metrics

For option 1 the only information you need to provide is the previously stated parameters which include: auth token, target, broker id, and config file

However, for option 2 in addition to the previously stated information, you will need to provide the hostname that Circonus will use to connect to your database, the username of the Postgres account that Circonus will use to connect to your database, the password for the username entered, and the name of any database that this user can connect to. Along with this, you will need to install the pg module using the command #npm install pg. This should be done before you run leo or else the software will fail to create you check, graphs, and worksheet.

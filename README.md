# MongoDB

## Configuring multiple VMs

![image](https://user-images.githubusercontent.com/129314018/233058390-c20d1c24-bfd4-4dba-b464-cd479fe4556d.png)

* We can change the name by adding `config.vm.define "app" do |app|`. 
* Change `app` to whatever name you want it to be.
* We then can change where `config` is to the VM name and in this case it is `app`.
* Be sure to add `end` to the `config ....` lines.

![image](https://user-images.githubusercontent.com/129314018/233061537-bcd45d79-97f0-4118-ae61-0a5c883d02f5.png)
* Be sure to comment out the code which deploys the app as it can cause vagrant to hand, the code in this case was `npm start`
* Virtual Machine(s) should be listed below in Virtualbox as such

![image](https://user-images.githubusercontent.com/129314018/233074885-9255bbe7-b536-4394-bd8f-fc4366eeff62.png)

## Provisioning MongoDB

1.  We create a new provision file for our db virtual machine, we name it `provisiondb.sh` and the contents are shown below :

```
# updates the package list on the Ubuntu system and installs the latest version of all packages.

sudo apt update -y

# upgrades all installed packages to the latest version.

sudo apt upgrade -y

# adds  MongoDB  key so we can authenticate packages from MongoDB repository

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927

# adds the MongoDB repository to the system's list of repositories

echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# We now update and upgrade again but now this includes the MongoDB repository and MongoDB to latest version

sudo apt update -y

sudo apt upgrade -y

# installs the MongoDB package and its associated components, including the server, shell, router, and tools

sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# starts the MongoDB service so that it is running on the system.

sudo systemctl start mongod
```
2.  We made this `provisiondb.sh` file with VScode, making sure it is in the same directory as the VagrantFile.

3.  On our VagrantFile we need to edit the config lines for db, and add a line for `db.vm.provision "shell", path: "provisiondb.sh"`

![image](https://user-images.githubusercontent.com/129314018/233094384-83e73626-2d8d-48de-ace2-bbc29c83d0cb.png)

4.  After `cd` into our folder where the VagrantFile is located, we run `vagrant up db` to load our db virtual machine with our preconfigured shell script to install mongodb.

5.  We then `vagrant ssh db` in our gitbash terminal, and once we are in, we do `sudo systemctl status mongod` to see if 
the installation of MongoDB has in fact been automated. The result is seen as in the image below.

![image](https://user-images.githubusercontent.com/129314018/233098024-0aefc07e-6eb4-42d5-a86b-4b0a3efeb935.png)







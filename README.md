# tech221_mongo

### Configuring multiple VMs

![image](https://user-images.githubusercontent.com/129314018/233058390-c20d1c24-bfd4-4dba-b464-cd479fe4556d.png)

* We can change the name by adding `config.vm.define "app" do |app|`. 
* Change `app` to whatever name you want it to be.
* We then can change where `config` is to the VM name and in this case it is `app`.
* Be sure to add `end` to the `config ....` lines.

![image](https://user-images.githubusercontent.com/129314018/233061537-bcd45d79-97f0-4118-ae61-0a5c883d02f5.png)
* Be sure to comment out the code which deploys the app as it can cause vagrant to hand, the code in this case was `npm start`
* Virtual Machine(s) should be listed below in Virtualbox as such

![image](https://user-images.githubusercontent.com/129314018/233074885-9255bbe7-b536-4394-bd8f-fc4366eeff62.png)


![image](https://user-images.githubusercontent.com/129314018/233080068-f67bde54-a1ab-449a-8f82-5ae186132f36.png)
![image](https://user-images.githubusercontent.com/129314018/233080546-31bf9e27-b906-4430-aa66-6327a814e229.png)


### Provisioning MongoDB

![image](https://user-images.githubusercontent.com/129314018/233094287-e5cf3ddd-b902-43fb-aac9-1a533f548183.png)
![image](https://user-images.githubusercontent.com/129314018/233094384-83e73626-2d8d-48de-ace2-bbc29c83d0cb.png)

After `cd` into our folder where the vagrantfile is located, we run `vagrant up db` to load our db virtual machine with our preconfigured shell script to install mongodb.

We then `vagrant ssh db` in our gitbash terminal, and once we are in, we do `sudo systemctl status mongod` to see if 
the installation of MongoDB has in fact been automated.

![image](https://user-images.githubusercontent.com/129314018/233095426-ced6b426-b2ee-4167-9388-e4a26c8e06fc.png)






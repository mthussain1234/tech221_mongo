# tech221_mongo

### Configuring multiple VMs

![image](https://user-images.githubusercontent.com/129314018/233058390-c20d1c24-bfd4-4dba-b464-cd479fe4556d.png)

* We can change the name by adding `config.vm.define "app" do |app|`. 
* Change `app` to whatever name you want it to be.
* We then can change where `config` is to the VM name and in this case it is `app`.
* Be sure to add `end` to the `config ....` lines.

![image](https://user-images.githubusercontent.com/129314018/233061537-bcd45d79-97f0-4118-ae61-0a5c883d02f5.png)
* Be sure to comment out the code which deploys the app as it can cause vagrant to hand, the code in this case was `npm start`


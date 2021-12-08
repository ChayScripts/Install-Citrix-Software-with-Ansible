# Install Citrix Software with Ansible

Install Citrix components like DDC, StoreFront, Director, Licensing using Ansible.

### Prerequisites

* PowerShell Remoting must be enabled on the Citrix servers (or run ```winrm quickconfig``` on the servers).
* Fully configured Ansible Controller Server.

### GroundWork

* Download the repo and:

  * Edit ServerList.txt file and add all your Citrix Server's ip addresses. 
  * Edit playbook.yml file and change the hosts or remove any software components that you dont want to install. You can install one component per iteration as well like installing only DDC or only Storefront component etc.. 
  * Download CVAD software from Citrix portal and extract the ISO contents to a share path. Update the share path file name in vars.yml file.

### Starting the installation

* Copy all the above files from this git repository to your ansible controller and edit as explained above.
* Navigate to the folder where you have the files and run any of the below command as applicable. The userid used below should have admin access on the Citrix Servers. 
```
ansible-playbook playbook.yml -i hosts.txt -e@vars.yml --extra-vars "ansible_user=administrator ansible_password=AdminPwd" -vvv
```
When using AD user,
```
ansible-playbook playbook.yml -i hosts.txt -e@vars.yml --extra-vars "ansible_user=domain\admin ansible_password=AdminPwd" -vvv
```
### Notes

* For director to work, it should be pointed to an existing Citrix site. So, if you install director software alone and try to login, it errors out. 
* Commands used in this repo are tested on CVAD 1912 LTSR version. In future, installation commands may change.

### Built With

* [PowerShell](https://en.wikipedia.org/wiki/PowerShell) - For installing the actual software
* [Ansible](https://docs.ansible.com/ansible/latest/index.html) - For invoking the install scripts

### Authors

* **Chay** - [ChayScripts](https://github.com/ChayScripts)
* Core Ansible script format is from: [Ryan's GitHub repo](https://github.com/ryancbutler/Citrix-VAD-LAB/tree/master/ansible)

### Contributing

Please follow [github flow](https://guides.github.com/introduction/flow/index.html) for contributing.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

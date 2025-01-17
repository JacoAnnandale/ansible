
03 Setting up the Git Repo
-------------------------------------------------------------


Check if git is installed

which git

Install git

sudo apt update
sudo apt install git

Create user config for git

git config --global user.name "First Last"
git config --global user.email "somebody@somewhere.net"

Check the status of your git repository

git status

Stage the README.md file (after making changes) to be included in the next git commit

git add README.md

Set up the README.md file to be included in a commit

git commit -m "Updated readme file, initial commit"

Send the commit to Github

git push origin master




04 Adhoc Commands
-------------------


https://www.learnlinux.tv/getting-started-with-ansible-04-executing-ad-hoc-commands/

Install ansible

 sudo apt update
 sudo apt install ansible

Create an inventory file (add the IP address for each server on its own line)

172.16.250.132
172.16.250.133
172.16.250.134

Add the inventory file to version control

 git add inventory

Commit the changes

 git commit -m "first version of the inventory file, added three hosts."

Push commit to Github

git push origin master

Test Ansible is working

ansible all --key-file ~/.ssh/ansible -i inventory -m ping

Create ansible config file

nano ansible.cfg
 
[defaults]
inventory = inventory private_key_file = ~/.ssh/ansible

Now the ansible command can be simplified

ansible all -m ping

List all of the hosts in the inventory

ansible all --list-hosts

Gather facts about your hosts

ansible all -m gather_facts

Gather facts about your hosts, but limit it to just one host

ansible all -m gather_facts --limit 172.16.250.132

# updates for master controller and target machines
#update  sudo apt update -y
sudo apt install net-tools
# passwordless authentication
ssh-keygen  for master controller

cd .ssh/
cat id_******.pub
# target machine 
cd .ssh/
vi authorisedkeys
Add in ssh-******* //

# Install Ansible on controller machine with script
run ./ansible.sh

# create inventory file on the controller
vi inventory(Add the ip address of the target machine)

# Test ansible connection to target machine
ansible -i inventory servers -m ping
ansible -i inventory all -m ping
ansible -i inventory servers -a "ls"
ansible -i inventory all -m shell -a 'df -h'

# Run the install-nginx from the controller on the target
./install-nginx.yml

# Confirm nginx service on target machine
sudo systemctl status nginx

# Run the install-apache from the controller on the target
./install-apache.yml

# Confirm apache service on target machine
sudo systemctl status apache

# To kill all the running process on the port 80

sudo apt-get install psmisc
sudo fuser 80/tcp sudo lsof -i tcp:80 
sudo lsof -i tcp:80 -s tcp:listen 
sudo lsof -t -i tcp:80 -s tcp:listen | sudo xargs kill

# To purge apache2

sudo apt-get purge apache2
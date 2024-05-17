#is a configuration tool
#if you have installed in one server you have take more server configuration from it
#aotumation like install docker on 10 servers like that
aws ec2
launch more like this ex 3 more
sudo apt install ansible
copy private key that is common in master node and 3 other
cd .ssh
vim ansible_key 
paste key in this esc:wq
cd ../
sudo ssh -i -/.ssh.ansible_key ubuntu@serverIP #private key name is ansible_key
you are now on an new server // exit
now you have to make inventory file on master node. Inventory file that contains all server information 
cat /etc/ansible/hosts if not in this follow next step
mkdir ansible
cd ansible
vim hosts
    -[servers]
    -server1 ansible_host=<severIP>
    -server2 ansible_host=<severIP>
    -server3 ansible_host=<severIP>
    -[all:vars]
    -ansible_pyhton_interpreter=/usr/bin/python3
    ecs:wq
ansible-inventory --list -y -i /hpme/ubuntu/ansible #to check inventory file is running or not
ansible all -m ping -i /home/ubuntu/ansible/hosts --private-key=-/.ssh/ansible_key #ping all client server with inventory path with ssh
chmod 700 /.ssh #make private key reachable
chmod 600 /.ssh/ansible
ansible all -a "free -h" -i /home/ubuntu/ansible/hosts --private-key=-/.ssh/ansible_key #for know how much RAM are in 
ansible servers -a "uptime" -i /home/ubuntu/ansible/hosts --private-key=-/.ssh/ansible_key



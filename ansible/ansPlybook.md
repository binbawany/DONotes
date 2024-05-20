#playbook is madeup of yml
#play is list of commands
#to automate ansible for configuration this is used
cd ansible
mkdir playbooks
cd playbooks
vim createfile.yml #to create in all servers
    ---     #three hyphin for start playbooks
    - name : this playbook is create file
      hosts : all
      become : true #means always as a superuser or rootuser
      tasks :                       #you can give in one playbook multiple task
        - name : create file
          file :
            path : /home/ubuntu/file.txt
            state : touch
    esc:wq
ansible-playbook createfile.yml -i /home/ubuntu/ansible/hosts --private-key=-/.ssh/ansible_key
#2nd playbook for create user envirement
vim create_user.yml
    ---
    - name : this play will create a user
      hosts : all
      become : true
      tasks :
        - name : to create username bin_bawany
          user : name=bin_bawany
    ecs:wq
ansible-playbook create_user.yml -i /home/ubuntu/ansible/hosts --private-key=-/.ssh/ansible_key
#go in 1 of client server
cat /etc/passwd         #linux command that is print all user in that server
ansible all -m apt -a "upgrade=yes update_cache=yes cache_valid_time=86400" --become i /home/ubuntu/ansible/hosts --private-key=-/.ssh/ansible_key #command for aupdate all
#3rd playbook for docker install
vim install_docker.yml
    ---
    - name : this play will install docker on all 
      hosts: all
      become : true
      tasks :
        - name : add Docker GPG apt key
          apt_key :
                url : https://download.docker.com/linux/ubuntu/gpg
                state : present

        - name : add Docker Repository
          apt_repository :
                repo : deb https://download.docker.com/linux/ubuntu/ focal stable
                state : present
        - name : install Docker
          apt :
                name : docker-co
                state : latest
          



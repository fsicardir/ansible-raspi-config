# ansible-raspi-config
I made this simple Ansible playbooks to automate the initial setup of my raspberry pi cluster.

## Prerequisites
1. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).
2. You need your own ssh key in `~/.ssh/id\_rsa.pub`.

## Usage
1. Set up your Ansible inventory in `/etc/ansible/hosts`. Mine, for example, looks like this:
    ```
    [raspi_cluster]
    192.168.0.104
    192.168.0.105
    192.168.0.106
    ```
2. Edit group\_vars/raspi\_cluster and replace "fransic" with the name you want for your user. 
3. Run `ansible-playbook raspi_user_and_key.yml`. This will create your new user and setup your credentials.
4. Run `ansible-playbook raspi_config.yml`. This will:
    - Set up sshd securely.
    - Change each hostname.
    - Remove the default pi user.
    - Update and upgrade all packages.
    - Install some basic packages.
    - Set up my dotfiles

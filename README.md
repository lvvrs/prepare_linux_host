# prepare_linux_host
Ansible playbook for prepare linux Hosts

# Functions

1. Playbook set hostname to hosts
2. Playbook add epel repository on rmp based hosts
3. Playbook install some packages to hosts (rpm and deb)
4. Playbook update packages on hosts
5. Playbook restart hosts and waith run hosts after reboot


# Run playbook on server with ansible-core

Command for run playbook:

    ansible-playbook -i hosts.ini -k -e "HOSTNAME_PREFIX=test DEBUG_FACTS=false" prepare-hosts.yml

where:

    -k - key for input password for ansible_user in local trminal
    -e - key for input environment variables
    DEBUG_FACTS - enable or disabel output ansible_facts in log
    HOSTNAME_PREFIX - variable set prefix in hostnames
    example:
       HOSTNAME_PREFIX = web-server
       server1 = webserver-HOSTNAME_END
       server2 = webserver-HOSTNAME_END
    HOSTNAME_END - set in hosts.ini file (must be unical for every server)
    example
       server1 = server-1
       server2 = server-2
    In result hostnames will be:
        server1 = webserver-server-1
        server2 = webserver-server-2

# Testing playbook

1. Test with ansible-lint

    
    ansible-lint -p prepare-hosts.yml -v

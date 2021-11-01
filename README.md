ansible-debian-11-hardening
==============================
This role applies security hardening configurations to systems running
Debian 11 (Bullseye).
These configurations include:
* AIDE -
* AppArmor
* Apt Package Manager
* Auditd + LAUREL
* ClamAV
* Fail2Ban
* Firewalld + nftables
* Hardened_Malloc
* Haveged
* Kernel tuning
* OpenSSH
* SysmonForLinux

Many of these configurations can be enabled/disabled in `defaults/main.yml`

Requirements
------------
Requires Ansible 2.10 or later. This role has only been tested on Debian 11 (Bullseye).

Role Variables
--------------
A large number of settings and configurations can be found in defaults/main.yml.

Dependencies
------------
None

Example Playbook
----------------

    - hosts: all
      become: yes
      become_method: sudo
      roles:
        - ansible-debian-11-hardening



Example Inventory
-----------------
*The `machine_hostname` variable is created for consistency when no DNS record exists*

*inventory.ini*

    [servers]
    192.168.0.11 ansible_ssh_user=admin machine_hostname=server01
    192.168.0.12 ansible_ssh_user=admin machine_hostname=server02
    192.168.0.13 ansible_ssh_user=admin machine_hostname=server03

*inventory.yml*

    ---
    all:
      hosts:
        192.168.0.11:
        192.168.0.12:
        192.168.0.13:
      vars:
        ansible_ssh_user: admin
        machine_hostname: server01

References
-----------
* <https://github.com/openstack/ansible-hardening>
* <https://madaidans-insecurities.github.io/guides/linux-hardening.html>
* <https://github.com/microsoft/MSTIC-Sysmon/tree/main/linux>
* <https://www.whonix.org/wiki/Hardened_Malloc>
* <https://github.com/threathunters-io/laurel>
* <https://wiki.archlinux.org/title/Security>

License
-------
GPL-3.0 License

Author Information
------------------
This role was created by Dan Kir

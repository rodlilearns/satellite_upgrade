# satellite_upgrade
Upgrade Red Hat Satellite

Link to the Satellite upgrade helper:
https://access.redhat.com/labs/satelliteupgradehelper/

6.8 -> 6.9 was chosen

Environment Parameters:
1. Connected
2. Not using capsules
3. Not using virt-who
4. Have installed the OpenSCAP plugin
5. Not using PXE-based discovery process

Steps:

1. ansible-playbook upgrade.yml -K <become_root_pass> --tags backup
2. ansible-playbook upgrade.yml -K <become_root_pass> --tags repos_and_packages
3. ansible-playbook upgrade.yml -K <become_root_pass> --tags upgrade
4. ansible-playbook upgrade.yml -K <become_root_pass> --tags reboot_if_needed
5. ansible-playbook upgrade.yml -K <become_root_pass> --tags restart_service
6. ansible-playbook upgrade.yml -K <become_root_pass> --tags sync
7. Manually configure the rest in the RH Satellite web UI.

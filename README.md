# nas_pi
####Ansible playbook to strip down the current raspbian release and set up Borg for NAS backups.

Update the *hosts* file to use the DNS name or IP of your Raspberry Pi in the [pis] group,<br />
Replace **roles/setup/files/naspi.pub** with the public SSH key you want to use to connect to Borg<br />
Edit the **/roles/setup/tasks/main.yml** file for your needs.

Note that the "Set up mount point in fstab" task in **/roles/setup/tasks/main.yml** is set up to mount an external disk labeled **/nas** formatted with the btrfs filesystem.  Setup of that disk is not handled here.

Once you've done that, run:
```bash
ansible-playbook setup.yml
```

This will probably take a while.

Afterwards make sure to change the password for the pi user, or remove that user.

TODO
- remove pi user
  - add admin user (with separate SSH key?) with sudo authority in setup playbook
  - add separate playbook to connect to pis as admin and remove pi user
  - or is there a way to do this in setup playbook?
- change sshd to disallow password access

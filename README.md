ansible-role-he-backup
======

This role perfoms the backup of the Hosted Engine DB to an NFS share exported via Ceph using Rados GW. When the backup is completed successfully, the playbook will send a message to a chat using a bot that you previously configured in Telegram.

Requirements
------------

* Running Ceph Cluster
* NFS Ganesha configured with the exported mountpoint
* Telegram Bot
* Telegram Bot Token
* Telegram ChatID

Play Variables
--------------

```
nfs_mount: /mnt/ceph-nfs
nfs_server: myhost.mydomain.com
nfs_path: hosted-backup
retention_days: 1w
yourbot_token: ....
yourbot_chatid: ....
```

Dependencies
------------

None

Example Playbook
----------------

```YAML
  - name: "RHV: Hosted Engine Backup"
    hosts: ovirt-engine
    become: yes
    tags: he-backup

    vars:
      nfs_mount: /mnt/ceph-nfs
      nfs_server: myhost.mydomain.com
      nfs_path: hosted-backup
      retention_days: 1w
      yourbot_token: ....
      yourbot_chatid: ....

    roles:
      - ansible-role-he-backup
```

License
-------

GPLv3

Author Information
------------------

Gianfranco Sigrisi wrote this role to automate the Hosted-Engine DB backup of his RHV Cluster.

# Ansible Role: ceph_storage

Role to prepare devices and validate config ahead of OSD creation.

## Validations
`lvm_volumes` is a list of dicts required by ceph-ansible that describes where
each OSD should locate its data, block.db and/or WAL. The devices can be varying types,
see RedHats documentation for full details, but ceph-ansible does not 
prepare the disks. This is what this role is for.

Ahead of creating the LVM config, the role will validate what has been passed to it in `validate.yml`

## Role Variables

Name | Description | Default Value
-----|------------|--------------
ceph_storage_devices | list of block devices to be used for object storage | None
ceph_storage_bluestore_volume_group | name to assign the bluestore volume group when WAL or block.db are not located on the storage device | block-db

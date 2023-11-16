+++
title = 'Hardware'
date = 2023-11-15T21:18:38-07:00
draft = false
+++

## Hardware Data

- Hardware data holds the details about the hardware that you wish to use with a workflow.
- A hardware may have multiple network devices that can be used in a worklfow.
- https://doc.crds.dev/github.com/tinkerbell/tink/tinkerbell.org/Hardware/v1alpha1@v0.9.0

## Example

If you have a hardware that has a single network/worker device on it, its hardware data shall be structured like the following:

```yaml
apiVersion: "tinkerbell.org/v1alpha1"
kind: Hardware
metadata:
  name: sm01
  namespace: default
spec:
  bmcRef:
    apiGroup: ""
    kind: ""
    name: ""
  disks:
    - device: /dev/nvme0n1
  interfaces:
    - dhcp:
        arch: x86_64
        hostname: sm01
        iface_name: ""
        ip:
          address: 172.16.10.100
          family: 4
          gateway: 172.16.10.1
          netmask: 255.255.255.0
        lease_time: 86400
        mac: 3c:ec:ef:4c:4f:54
        name_servers:
          - 172.16.10.1
          - 10.1.1.11
        uefi: true
        vlan_id: ""
      netboot:
        allowPXE: true
        allowWorkflow: true
        ipxe:
          contents: ""
          url: ""
        osie:
          baseURL: ""
          initrd: ""
          kernel: ""
  metadata:
    bonding_mode: ""
    custom:
      preinstalled_operating_system_version:
        distro: ""
        image_tag: ""
        os_slug: ""
        slug: ""
        version: ""
      private_subnets:
        - ""
    facility:
      facility_code: onprem
      plan_slug: ""
      plan_version_slug: ""
    instance:
      allow_pxe: true
      always_pxe: true
      crypted_root_password: ""
      hostname: "sm01"
      id: "3c:ec:ef:4c:4f:54"
      ips:
        - address: ""
          family: 4
          gateway: ""
          management: true
          netmask: ""
          public: true
      ipxe_script_url: ""
      network_ready: true
      operating_system:
        distro: "ubuntu"
        image_tag: ""
        os_slug: "ubuntu_20_04"
        slug: ""
        version: "20.04"
      rescue: false
      ssh_keys:
        - ""
      state: ""
      storage:
        disks:
          - device: ""
            partitions:
              label: ""
              number: 1
              size: 1
              start: 1
              type_guid: ""
            wipe_table: true
        filesystems:
          - mount:
              create:
                force: true
                options:
                  - ""
              device: ""
              files:
                - contents: ""
                  gid: 0
                  mode: 0600
                  path: ""
                  uid: 0
              format: ""
              point: ""
        raid:
          - devices:
              - ""
            level: ""
            name: ""
            spare: 0
      tags:
        - ""
      userdata: ""
    manufacturer:
      id: ""
      slug: supermicro
    state: ""
  userData: ""
  vendorData: ""
```

## Property Description

The following section explains each property in the above example:

| Property                                                     | Description                                                                                                                                                                                                                                    |
| ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                                                           | An identifier used to uniquely identify the hardware. The `id` can be generated using the `uuidgen` command. If you are in Equinix Metal environment, you can get the `id` from the server overview page. The `id` doesn't _have_ to be a UUID, provided it's unique.                                          |
| network                                                      | Network details                                                                                                                                                                                                                                |
| network.Interfaces[]                                         | List of network interfaces on the hardware                                                                                                                                                                                                     |
| network.interfaces[].dhcp                                    | DHCP details                                                                                                                                                                                                                                   |
| network.interfaces[].dhcp.mac                                | MAC address of the network device (worker)                                                                                                                                                                                                     |
| network.interfaces[].dhcp.ip                                 | IP details for DHCP                                                                                                                                                                                                                            |
| network.interfaces[].dhcp.ip.address                         | Worker IP address to be requested over DHCP                                                                                                                                                                                                    |
| network.interfaces[].dhcp.ip.gateway                         | Gateway address                                                                                                                                                                                                                                |
| network.interfaces[].dhcp.ip.netmask                         | Netmask for the private network                                                                                                                                                                                                                |
| network.interfaces[].dhcp.hostname                           | Hostname                                                                                                                                                                                                                                       |
| network.interfaces[].dhcp.lease_time                         | Expiration in secs (default: 86400)                                                                                                                                                                                                            |
| network.interfaces[].dhcp.name_servers[]                     | DNS servers                                                                                                                                                                                                                                    |
| network.interfaces[].dhcp.time_servers[]                     | NTP servers                                                                                                                                                                                                                                    |
| network.interfaces[].dhcp.arch                               | Hardware architecture, example: `x86_64`                                                                                                                                                                                                       |
| network.interfaces[].dhcp.uefi                               | Is UEFI                                                                                                                                                                                                                                        |
| network.interfaces[].netboot                                 | Netboot details                                                                                                                                                                                                                                |
| network.interfaces[].netboot.allow_pxe                       | Must be set to `true` to PXE.                                                                                                                                                                                                                  |
| network.interfaces[].netboot.allow_workflow                  | Must be `true` in order to execute a workflow.                                                                                                                                                                                                 |
| network.interfaces[].netboot.ipxe                            | Details for iPXE                                                                                                                                                                                                                               |
| network.interfaces[].netboot.ipxe.url                        | iPXE script URL                                                                                                                                                                                                                                |
| network.interfaces[].netboot.ipxe.contents                   | iPXE script contents                                                                                                                                                                                                                           |
| network.interfaces[].netboot.osie                            | OSIE details                                                                                                                                                                                                                                   |
| network.interfaces[].netboot.osie.kernel                     | Kernel                                                                                                                                                                                                                                         |
| network.interfaces[].netboot.osie.initrd                     | Initrd                                                                                                                                                                                                                                         |
| network.interfaces[].netboot.osie.base_url                   | Base URL for the kernel and initrd                                                                                                                                                                                                             |
| metadata                                                     | Hardware metadata details                                                                                                                                                                                                                      |
| metadata.state                                               | State must be set to `provisioning` for workflows.                                                                                                                                                                                             |
| metadata.bonding_mode                                        | Bonding mode                                                                                                                                                                                                                                   |
| metadata.manufacturer                                        | Manufacturer details                                                                                                                                                                                                                           |
| metadata.instance                                            | Holds the details for an instance                                                                                                                                                                                                              |
| metadata.instance.storage                                    | Details for an instance storage like disks and filesystems                                                                                                                                                                                     |
| metadata.instance.storage.disks                              | List of disk partitions                                                                                                                                                                                                                        |
| metadata.instance.storage.disks[].device                     | Name of the disk                                                                                                                                                                                                                               |
| metadata.instance.storage.disks[].wipe_table                 | Set to `true` to allow disk wipe.                                                                                                                                                                                                              |
| metadata.instance.storage.disks[].partitions                 | List of disk partitions                                                                                                                                                                                                                        |
| metadata.instance.storage.disks[].partitions[].size          | Size of the partition                                                                                                                                                                                                                          |
| metadata.instance.storage.disks[].partitions[].label         | Partition label like BIOS, SWAP or ROOT                                                                                                                                                                                                        |
| metadata.instance.storage.disks[].partitions[].number        | Partition number                                                                                                                                                                                                                               |
| metadata.instance.storage.filesystems                        | List of filesystems and their respective mount points                                                                                                                                                                                          |
| metadata.instance.storage.filesystems[].mount                | Details about the filesystem to be mounted                                                                                                                                                                                                     |
| metadata.instance.storage.filesystems[].mount.point          | Mount point for the filesystem                                                                                                                                                                                                                 |
| metadata.instance.storage.filesystems[].mount.create         | Additional details that can be provided while creating a partition                                                                                                                                                                             |
| metadata.instance.storage.filesystems[].mount.create.options | Options to be passed to `mkfs` while creating a partition                                                                                                                                                                                      |
| metadata.instance.storage.filesystems[].mount.device         | Device to be mounted                                                                                                                                                                                                                           |
| metadata.instance.storage.filesystems[].mount.format         | Filesystem format                                                                                                                                                                                                                              |
| metadata.instance.crypted_root_password                      | Hash for root password that is used to login into the worker after provisioning. The hash can be generated using the `openssl passwd` command. For example, `openssl passwd -6 -salt xyz your-password`.                                       |
| metadata.operating_system_version                            | Details about the operating system to be installed                                                                                                                                                                                             |
| metadata.operating_system_version.distro                     | Operating system distribution name, like ubuntu                                                                                                                                                                                                |
| metadata.operating_system_version.version                    | Operating system version, like 18.04 or 20.04                                                                                                                                                                                                  |
| metadata.operating_system_version.os_slug                    | A slug is a combination of operating system distro and version.                                                                                                                                                                                |
| metadata.facility                                            | Facility details                                                                                                                                                                                                                               |
| metadata.facility.plan_slug                                  | The slug for the worker class. The value for this property depends on how you setup your workflow. While it is required if you are using the OS images from [packet-images] repository, it may be left out if not used at all in the workflow. |
| metadata.facility.facility_code                              | For local setup, `onprem` or any other string value can be used.                                                                                                                                                                               |

## The Minimal Hardware Data

While the hardware data is essential, not all the properties are required for every workflow.

```json
apiVersion: "tinkerbell.org/v1alpha1"
kind: Hardware
metadata:
  name: sm01
  namespace: default
spec:
  disks:
    - device: /dev/nvme0n1
  metadata:
    facility:
      facility_code: onprem
    manufacturer:
      slug: supermicro
    instance:
      userdata: ""
      hostname: "sm01"
      id: "3c:ec:ef:4c:4f:54"
      operating_system:
        distro: "ubuntu"
        os_slug: "ubuntu_20_04"
        version: "20.04"
  interfaces:
    - dhcp:
        arch: x86_64
        hostname: sm01
        ip:
          address: 172.16.10.100
          gateway: 172.16.10.1
          netmask: 255.255.255.0
        lease_time: 86400
        mac: 3c:ec:ef:4c:4f:54
        name_servers:
          - 172.16.10.1
          - 10.1.1.11
        uefi: true
      netboot:
        allowPXE: true
        allowWorkflow: true
```

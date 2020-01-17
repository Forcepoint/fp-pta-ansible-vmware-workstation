# vmware-workstation

Install VMware Workstation.

## Requirements

You must host the VMware Workstation Pro bundle on a web server. Doing so with Artifactory in a local
generic repository is a viable option.
VMWare does not provide the installer without authentication on their
website. It is a pain. Requiring self hosting of the binary seemed a simpler solution than trying
to automate the download from them.

## Role Variables

### REQUIRED

* vmware_workstation_download_url: A URL to download the VMware Workstation Pro bundle from.
* vmware_workstation_checksum: The checksum of the VMware Workstation Pro bundle.
* vmware_workstation_serial_num: The serial number with dashes from your VMware Workstation license. Be sure you vault this. 
* vmware_workstation_version: The version of VMware Workstation Pro that's to be installed. 
  This is for checking if the install is needed.

### OPTIONAL

None

## Dependencies

None

## Example Playbook

    - hosts: servers
      vars:
        vmware_workstation_download_url: https://artifactory.COMPANY.com/artifactory/software/VMware/VMware-Workstation-Full-14.1.2-8497320.x86_64.bundle
        vmware_workstation_checksum: sha256:8932c681a8954c4aaf0e7d0039c6d8dff9ade323170d9a9a78553c98ffe16963
        vmware_workstation_serial_num: "xxxxx-xxxxx-xxxxx-xxxxx-xxxxx"
        vmware_workstation_version: 14.1.2
      roles:
      - role: pta-packer

## License

BSD

## Author Information

Jeremy Cornett <jeremy.cornett@forcepoint.com>

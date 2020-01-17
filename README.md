# vmware-workstation

Setup a CentOS system with VMware Workstation Pro. 
It is normally desirable to have a GUI, and the GNOME Desktop is suggested.

## Requirements

You have a working Artifactory instance over HTTPS which is hosting the VMware Workstation installer
in a local generic repository. VMWare does not provide the installer without authentication on their
website. It is a pain. Requiring self hosting of the binary seemed a simpler solution than trying
to automate the download from them.

## Role Variables

### REQUIRED

* vmware_workstation_artifactory: The DNS name of your Artifactory server.
* vmware_workstation_serial_num: The serial number with dashes from your VMware Workstation license. Be sure you vault this. 

### OPTIONAL

* vmware_workstation_version: The version of VMware Workstation Pro to install.
* vmware_workstation_build: The build number of VMware Workstation Pro to install.
* vmware_workstation_checksum: The checksum of the VMware Workstation Pro bundle.
* vmware_workstation_artifactory: The Artifactory DNS name to download the VMware Workstation 
  Prod bundle from. VMWare does not make this binary publicly available so you have to store it somewhere
  in artifactory and download it from there.

## Dependencies

None

## Example Playbook

    - hosts: servers
      vars:
        vmware_workstation_version: 14.1.2
        vmware_workstation_build: 8497320
        vmware_workstation_checksum: sha256:8932c681a8954c4aaf0e7d0039c6d8dff9ade323170d9a9a78553c98ffe16963
        vmware_workstation_artifactory: artifactory.COMPANY.com
        vmware_workstation_serial_num: "xxxxx-xxxxx-xxxxx-xxxxx-xxxxx"
      roles:
      - role: pta-packer

## License

BSD

## Author Information

Jeremy Cornett <jeremy.cornett@forcepoint.com>

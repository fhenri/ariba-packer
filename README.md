This creates a vagrant box to deploy an Ariba instance. The provisioning is not done in packer but in vagrant (see ariba-vagrant project)
The script are largely inspired from the basebox-packer project

The definition of the box is :
- create an ariba user (no password defined)
- root password is ariba
- 40 Gb defined (enough to install 3rd party software and run with large db)
- choose your preference of provisionner (chef, puppet or other)

To build it, I personnaly use the following command
    `packer build -var "cm=puppet" -var "cm_version=3.8.5" -only vmware-iso centos7.json`

Add the VM to vagrant
    `vagrant box add --name cloud06/ariba-puppet-centos71 centos7-puppet-3.8.5-vmware-1.0.1.box`

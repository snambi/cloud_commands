
# Create an image for openstack
http://docs.openstack.org/image-guide/ubuntu-image.html

virt-install doesn't work with the image created by qemu-img.
It results in space not enough error when partitioning the drive.
Instead, use the ISO image directly with virt-manager 

## Get information about an qcow2 image
qemu-img info <file>.qcow2

## create a qcow2 image 
qemu-img create -f qcow2 myimg.qcow2 10G

## install an OS on the above image ( the disk partitioning has issues in this command )
virt-install --virt-type kvm --name trusty-mini --ram 512 --cdrom=/home/snambi/Downloads/mini.iso --disk /home/snambi/projects/os_images/trusty.qcow2 --network network=default  --graphics vnc,listen=0.0.0.0  --noautoconsole  --os-type=linux --os-variant=ubuntutrusty

## get details about and KVM image
virsh dumpxml <vm-name>

## start a VM in paused mode
virsh start <vm-name> --paused

## resume the VM
virsh resume <vm-name>


# Create an image for openstack
http://docs.openstack.org/image-guide/ubuntu-image.html

virt-install doesn't work with the image created by qemu-img.
It results in space not enough error when partitioning the drive.
Instead, use the ISO image directly with virt-manager 



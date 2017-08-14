# packer-esxi

A set of example [Packer][] templates for building Debian and Ubuntu boxes on
[VMware ESXi][]. These are built on the remote ESXi host, then shutdown and
left registered.

They assume that it's possible to fetch an IP through DHCP on the primary (`VM
Network`) network or whatever you've configured the network to be in `variables.json`.
If this doesn't work, you can adjust the [boot command to set a static IP][].

This example repo comes out of [this post I wrote on how to use Packer with
VMware ESXi][post].


## Prep-work

###### Configure variables.json
The `variables.json` file is gitignored and contains variables referenced by the packer scripts such as the ESXi server address and default root passwords.

###### ESXi setup
Run python_esxi on a fresh install of ESXi to set it up for building VMs.

###### Preseed and Debian
Note that debian removed support for Floppy Disks in version 8 and 9 because it was "really confusing stuff" and "seem[ed] hardly useful for anyone, anywhere" so you'll need to host preseed files somewhere safe and update their locations in the variables.json file.  If you update things, don't forget to update their checksums too!


## Usage

```sh
./build ubuntu-1604-base.json
```


## Testing Boxes

A Vagrantfile was borrowed from https://github.com/geerlingguy/packer-debian-9 and a the `.json` and `preseed` stuff for enabling debian 9.  To boot into a box and dig around on the local machine, just run:

```
$ vagrant up debian9
$ vagrant ssh debian9
# (NOTE:  I'm still making this work...)
```


## Original Author

(NOTE:  TheNotary added the snarky comments here and there)

Copyright (c) 2016 Nick Charlton. MIT Licensed.

[Packer]: https://packer.io
[VMware ESXi]: http://www.vmware.com/products/vsphere-hypervisor.html
[boxes]: https://github.com/nickcharlton/boxes
[boot command to set a static IP]: https://help.ubuntu.com/lts/installation-guide/armhf/apbs02.html
[post]: https://nickcharlton.net/posts/using-packer-esxi-6.html
